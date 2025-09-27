[index.html](https://github.com/user-attachments/files/22317827/index.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Suporte Estacionamento Vertical</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">

  <style>
    body {
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(135deg, #f4f4f4, #e0e0e0);
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }
    .container {
      background: #fff;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0px 4px 12px rgba(0,0,0,0.2);
      max-width: 400px;
      width: 100%;
      text-align: center;
    }
    h1, h2 {
      color: #333;
    }
    input, button {
      margin: 10px 0;
      padding: 10px;
      width: 90%;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
    button {
      background: #007bff;
      color: white;
      font-weight: bold;
      cursor: pointer;
      border: none;
    }
    button:hover { background: #0056b3; }

    .stars {
      display: flex;
      justify-content: center;
      gap: 5px;
      margin: 10px 0;
    }
    .star {
      font-size: 28px;
      cursor: pointer;
      color: gray;
      transition: 0.2s;
    }
    .star.selected { color: gold; }

    .menu { display: flex; flex-direction: column; gap: 15px; margin-top: 20px; }
    .menu a {
      display: block;
      background: #007bff;
      color: white;
      text-decoration: none;
      padding: 12px;
      border-radius: 8px;
      font-weight: 500;
    }
    .menu a:hover { background: #0056b3; }

    .emergencia { background: #e74c3c !important; }
    .emergencia:hover { background: #c0392b !important; }

    #painelProgramador { display: none; margin-top: 30px; }
    table { width: 100%; border-collapse: collapse; margin-top: 10px; }
    th, td { border: 1px solid #ccc; padding: 8px; text-align: center; }
    th { background: #007bff; color: white; }
  </style>
</head>
<body>

<div class="container" id="telaInicial">
  <h1>Bem-vindo</h1>
  <p>Preencha os dados e avalie o Projeto:</p>
  <input type="text" id="nome" placeholder="Digite seu nome" required>
  <input type="number" id="idade" placeholder="Digite sua idade" required min="1">

  <p>Avalie o Projeto:</p>
  <div class="stars" id="starsProjeto">
    <span class="star" data-value="1">★</span>
    <span class="star" data-value="2">★</span>
    <span class="star" data-value="3">★</span>
    <span class="star" data-value="4">★</span>
    <span class="star" data-value="5">★</span>
  </div>
  <button id="btnProjeto">Enviar Avaliação</button>
</div>

<div class="container" id="telaSuporte" style="display:none;">
  <h1>📲 Suporte - Estacionamento Vertical</h1>
  <div class="menu">
    <a href="#">🚧 Elevador parado</a>
    <a href="#">⏳ Muito tempo de espera</a>
    <a href="#">ℹ️ Informações</a>
    <a href="https://wa.me/5511958276139" target="_blank">💬 WhatsApp</a>
    <a class="emergencia" href="tel:190">🚔 Polícia (190)</a>
    <a class="emergencia" href="tel:193">🚒 Bombeiros (193)</a>
  </div>

  <h2>Avalie o Aplicativo</h2>
  <div class="stars" id="starsApp">
    <span class="star" data-value="1">★</span>
    <span class="star" data-value="2">★</span>
    <span class="star" data-value="3">★</span>
    <span class="star" data-value="4">★</span>
    <span class="star" data-value="5">★</span>
  </div>
  <button id="btnApp">Enviar Avaliação do App</button>

  <!-- Painel Programador -->
  <div id="painelProgramador">
    <h2>Painel do Programador</h2>
    <table>
      <tr><th>Tipo</th><th>Quantidade</th><th>Média</th></tr>
      <tr><td>Projeto</td><td id="qtdProjeto">0</td><td id="mediaProjeto">0</td></tr>
      <tr><td>Aplicativo</td><td id="qtdApp">0</td><td id="mediaApp">0</td></tr>
    </table>
  </div>
</div>

<script>
  let avaliacoesProjeto = [];
  let avaliacoesApp = [];

  function configurarEstrelas(containerId) {
    const stars = document.querySelectorAll(`#${containerId} .star`);
    stars.forEach(star => {
      star.addEventListener("click", () => {
        const value = star.getAttribute("data-value");
        stars.forEach(s => s.classList.remove("selected"));
        for (let i = 0; i < value; i++) { stars[i].classList.add("selected"); }
        document.getElementById(containerId).setAttribute("data-selected", value);
      });
    });
  }
  configurarEstrelas("starsProjeto");
  configurarEstrelas("starsApp");

  function atualizarPainel() {
    document.getElementById("qtdProjeto").innerText = avaliacoesProjeto.length;
    document.getElementById("mediaProjeto").innerText =
      avaliacoesProjeto.length > 0 ? (avaliacoesProjeto.reduce((a,b)=>a+b,0) / avaliacoesProjeto.length).toFixed(1) : 0;
    document.getElementById("qtdApp").innerText = avaliacoesApp.length;
    document.getElementById("mediaApp").innerText =
      avaliacoesApp.length > 0 ? (avaliacoesApp.reduce((a,b)=>a+b,0) / avaliacoesApp.length).toFixed(1) : 0;
  }

  // Avaliação Projeto
  document.getElementById("btnProjeto").addEventListener("click", () => {
    const nome = document.getElementById("nome").value;
    const idade = document.getElementById("idade").value;
    const estrelas = parseInt(document.getElementById("starsProjeto").getAttribute("data-selected")) || 0;

    if (!nome || !idade) { alert("Preencha nome e idade."); return; }
    if (estrelas === 0) { alert("Escolha uma nota para o projeto."); return; }

    avaliacoesProjeto.push(estrelas);
    alert(`Obrigado ${nome}, ${idade} anos!\nSua avaliação do Projeto foi ${estrelas} estrela(s).`);

    atualizarPainel();
    document.getElementById("telaInicial").style.display = "none";
    document.getElementById("telaSuporte").style.display = "block";

    // Checa senha do programador
    const senha = prompt("Digite a senha do programador ou deixe vazio para continuar:");
    if (senha === "admin123") {
      document.getElementById("painelProgramador").style.display = "block";
    }
  });

  // Avaliação App
  document.getElementById("btnApp").addEventListener("click", () => {
    const estrelas = parseInt(document.getElementById("starsApp").getAttribute("data-selected")) || 0;
    if (estrelas === 0) { alert("Escolha uma nota para o aplicativo."); return; }
    avaliacoesApp.push(estrelas);
    alert(`Obrigado pela sua avaliação do App: ${estrelas} estrela(s).`);
    atualizarPainel();
    document.querySelectorAll("#starsApp .star").forEach(s=>s.classList.remove("selected"));
    document.getElementById("starsApp").removeAttribute("data-selected");
  });
</script>

</body>
</html>