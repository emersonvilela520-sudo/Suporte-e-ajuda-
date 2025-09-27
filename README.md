[index.html](https://github.com/user-attachments/files/22317827/index.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Estacionamento Vertical - Suporte</title>

  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">

  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(135deg, #f4f4f4, #e0e0e0);
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
      padding: 20px;
    }

    h1, h2 {
      color: #333;
      margin: 20px 0;
      text-align: center;
    }

    .menu {
      display: flex;
      flex-direction: column;
      gap: 15px;
      width: 100%;
      max-width: 400px;
      margin-bottom: 40px;
    }

    .menu a {
      text-decoration: none;
      background: #007bff;
      color: white;
      padding: 15px;
      border-radius: 12px;
      font-size: 18px;
      font-weight: 500;
      text-align: center;
      transition: transform 0.3s, background 0.3s, box-shadow 0.3s;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    }

    .menu a:hover {
      background: #0056b3;
      transform: translateY(-3px);
      box-shadow: 0 6px 10px rgba(0,0,0,0.15);
    }

    .emergencia { background: #e74c3c; }
    .emergencia:hover { background: #c0392b; }

    .modal {
      display: none;
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      backdrop-filter: blur(4px);
      background: rgba(0,0,0,0.4);
      justify-content: center;
      align-items: center;
      z-index: 10;
    }

    .modal-content {
      background: #fff;
      padding: 30px;
      border-radius: 12px;
      max-width: 500px;
      text-align: center;
      position: relative;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
    }

    .close-btn {
      position: absolute;
      top: 10px; right: 15px;
      font-size: 20px;
      cursor: pointer;
      color: #555;
    }
    .close-btn:hover { color: #000; }

    .form-container {
      background: #fff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0px 4px 8px rgba(0,0,0,0.2);
      max-width: 400px;
      margin: 20px auto;
    }

    input, button {
      margin: 10px 0;
      padding: 8px;
      width: 90%;
      border: 1px solid #ccc;
      border-radius: 8px;
    }

    button {
      background: #28a745;
      color: white;
      font-weight: bold;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover { background: #218838; }

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
      transition: color 0.2s;
    }
    .star.selected { color: gold; }

    #painelProgramador {
      display: none; /* Escondido por padrão */
    }

    table {
      margin: 20px auto;
      border-collapse: collapse;
      width: 90%;
      background: #fff;
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0px 4px 8px rgba(0,0,0,0.2);
    }

    th, td {
      padding: 10px;
      border: 1px solid #ccc;
    }
    th { background: #007BFF; color: white; }
  </style>
</head>
<body>

  <h1>📲 Suporte e Ajuda - Estacionamento Vertical</h1>

  <div class="menu">
    <a href="#" onclick="openModal('Elevador parado')">🚧 Elevador parado</a>
    <a href="#" onclick="openModal('Muito tempo de espera')">⏳ Muito tempo de espera</a>
    <a href="#" onclick="openModal('Informações gerais')">ℹ️ Informações</a>
    <a href="https://wa.me/5511958276139" target="_blank" rel="noopener noreferrer">💬 WhatsApp</a>
    <a class="emergencia" href="tel:190">🚔 Emergência Policial (190)</a>
    <a class="emergencia" href="tel:193">🚒 Emergência Bombeiros (193)</a>
    <a href="https://emersonvilela520-sudo.github.io/estacionamento-projeto/"
       target="_blank" rel="noopener noreferrer">🌐 Site</a>
    <a href="#" onclick="openModal('Reclamações')">📢 Reclamações</a>
  </div>

  <!-- Modal -->
  <div id="modal" class="modal">
    <div class="modal-content">
      <span class="close-btn" onclick="closeModal()">&times;</span>
      <h2 id="modal-title">Título</h2>
      <p id="modal-text">Conteúdo da informação.</p>
    </div>
  </div>

  <!-- Avaliação Projeto -->
  <h2>Avaliação do Projeto</h2>
  <div class="form-container">
    <form id="formProjeto">
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
      <button type="submit">Enviar Avaliação do Projeto</button>
    </form>
  </div>

  <!-- Avaliação App -->
  <h2>Avaliação do Aplicativo</h2>
  <div class="form-container">
    <p>Avalie o Aplicativo:</p>
    <div class="stars" id="starsApp">
      <span class="star" data-value="1">★</span>
      <span class="star" data-value="2">★</span>
      <span class="star" data-value="3">★</span>
      <span class="star" data-value="4">★</span>
      <span class="star" data-value="5">★</span>
    </div>
    <button id="btnApp">Enviar Avaliação do App</button>
  </div>

  <!-- Painel Programador (oculto por padrão) -->
  <div id="painelProgramador">
    <h2>Painel do Programador</h2>
    <table>
      <tr>
        <th>Tipo</th>
        <th>Quantidade</th>
        <th>Média de Estrelas</th>
      </tr>
      <tr>
        <td>Projeto</td>
        <td id="qtdProjeto">0</td>
        <td id="mediaProjeto">0</td>
      </tr>
      <tr>
        <td>Aplicativo</td>
        <td id="qtdApp">0</td>
        <td id="mediaApp">0</td>
      </tr>
    </table>
  </div>

  <script>
    // Mensagens para modal
    const mensagens = {
      "Elevador parado": "O elevador encontra-se temporariamente fora de operação. Nossa equipe técnica já foi acionada para resolver o problema.",
      "Muito tempo de espera": "O tempo de espera pode aumentar em horários de pico. Pedimos a compreensão e paciência de todos os usuários.",
      "Informações gerais": "Este estacionamento vertical foi projetado para otimizar espaço e aumentar a segurança. Em caso de dúvidas, entre em contato pelo WhatsApp.",
      "Reclamações": "Para registrar sua reclamação, utilize o botão do WhatsApp ou entre em contato com a administração."
    };

    function openModal(title) {
      document.getElementById('modal-title').innerText = title;
      document.getElementById('modal-text').innerText = mensagens[title] || "Informação não disponível.";
      document.getElementById('modal').style.display = 'flex';
    }
    function closeModal() { document.getElementById('modal').style.display = 'none'; }
    window.onclick = function(event) {
      const modal = document.getElementById('modal');
      if (event.target == modal) { modal.style.display = "none"; }
    }

    // Avaliações
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
        avaliacoesProjeto.length > 0
          ? (avaliacoesProjeto.reduce((a,b)=>a+b,0) / avaliacoesProjeto.length).toFixed(1)
          : 0;

      document.getElementById("qtdApp").innerText = avaliacoesApp.length;
      document.getElementById("mediaApp").innerText =
        avaliacoesApp.length > 0
          ? (avaliacoesApp.reduce((a,b)=>a+b,0) / avaliacoesApp.length).toFixed(1)
          : 0;
    }

    // Projeto
    document.getElementById("formProjeto").addEventListener("submit", function(e) {
      e.preventDefault();
      const nome = document.getElementById("nome").value;
      const idade = document.getElementById("idade").value;
      const estrelas = parseInt(document.getElementById("starsProjeto").getAttribute("data-selected")) || 0;

      if (estrelas === 0) { alert("Por favor, selecione uma nota para o projeto."); return; }

      avaliacoesProjeto.push(estrelas);
      alert(`Obrigado ${nome}, ${idade} anos!\nSua avaliação do projeto foi ${estrelas} estrela(s).`);

      atualizarPainel();
      e.target.reset();
      document.querySelectorAll("#starsProjeto .star").forEach(s=>s.classList.remove("selected"));
      document.getElementById("starsProjeto").removeAttribute("data-selected");
    });

    // App
    document.getElementById("btnApp").addEventListener("click", function() {
      const estrelas = parseInt(document.getElementById("starsApp").getAttribute("data-selected")) || 0;
      if (estrelas === 0) { alert("Por favor, selecione uma nota para o aplicativo."); return; }

      avaliacoesApp.push(estrelas);
      alert(`Obrigado pela sua avaliação do app: ${estrelas} estrela(s).`);

      atualizarPainel();
      document.querySelectorAll("#starsApp .star").forEach(s=>s.classList.remove("selected"));
      document.getElementById("starsApp").removeAttribute("data-selected");
    });

    // --- Acesso do programador ---
    const senhaProgramador = "admin123"; // senha definida
    const acesso = prompt("Digite a senha do programador ou deixe vazio para usuário comum:");
    if (acesso === senhaProgramador) {
      document.getElementById("painelProgramador").style.display = "block";
    }
  </script>
</body>
</html>