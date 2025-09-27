[index.html](https://github.com/user-attachments/files/22317827/index.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Estacionamento Vertical Automatizado — Colégio Pentágono</title>
  <meta name="description" content="Projeto de Estacionamento Vertical Automatizado — Curso Técnico em Mecatrônica, Colégio Pentágono.">
  <style>
    :root{
      --bg:#f7f8fb;
      --card:#fff;
      --accent:#0b63d6;
      --muted:#6b7280;
      --danger:#e74c3c;
      --maxw:1000px;
    }

    *{box-sizing:border-box;margin:0;padding:0}
    body{
      font-family:Inter, Roboto, system-ui, -apple-system, "Segoe UI", Arial;
      line-height:1.5;
      background:var(--bg);
      color:#111;
      scroll-behavior:smooth;
    }

    .container{max-width:var(--maxw);margin:20px auto;padding:10px}
    header{display:flex;gap:16px;align-items:center;flex-wrap:wrap;position:sticky;top:0;background:var(--bg);padding:10px 0;z-index:1000}
    .brand{display:flex;flex-direction:column;flex:1}
    h1{margin:0;font-size:1.5rem}
    .subtitle{color:var(--muted);font-size:0.9rem}
    .card{
      background:var(--card);
      padding:15px;
      border-radius:12px;
      box-shadow:0 6px 18px rgba(12,18,35,0.06);
      margin-top:15px;
      transition:transform 0.2s;
    }
    .card:hover{transform:translateY(-3px)}
    nav{display:flex;flex-wrap:wrap;gap:10px;margin-top:12px;position:sticky;top:72px;background:var(--bg);padding:5px 0;z-index:999;}
    nav a{
      color:var(--accent);
      text-decoration:none;
      border:1px solid transparent;
      padding:6px 8px;
      border-radius:8px;
      font-size:0.9rem;
    }
    nav a:hover{background:rgba(11,99,214,0.07)}
    .grid{display:flex;flex-direction:column;gap:15px;margin-top:10px}
    main{flex:3}
    .section h2{margin-top:0}
    .meta{font-size:0.85rem;color:var(--muted);margin-bottom:6px}
    ul.team{padding-left:1rem;margin-bottom:0}
    img{max-width:100%;border-radius:8px;margin-top:10px;display:block;cursor:pointer;transition:transform 0.2s}
    img:hover{transform:scale(1.02)}
    footer{text-align:center;color:var(--muted);font-size:0.85rem;margin-top:20px}

    /* Botões de suporte */
    .menu{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      margin-top:10px;
    }
    .menu a{
      text-decoration:none;
      padding:10px;
      border-radius:8px;
      font-size:0.9rem;
      text-align:center;
      flex:1 1 calc(50% - 10px);
      background:var(--accent);
      color:#fff;
      transition:0.3s;
    }
    .menu a:hover{background:#0056b3}
    .emergencia{background:var(--danger)}
    .emergencia:hover{background:#c0392b}

    /* Modal */
    .modal{
      display:none;
      position:fixed;
      top:0;left:0;width:100%;height:100%;
      backdrop-filter:blur(4px);
      background:rgba(0,0,0,0.6);
      justify-content:center;
      align-items:center;
      z-index:2000;
    }
    .modal-content{
      background:#fff;
      padding:20px;
      border-radius:12px;
      max-width:90%;
      max-height:90%;
      text-align:center;
      position:relative;
      overflow:auto;
    }
    .modal-content img{max-width:100%;height:auto;border-radius:8px;margin-top:0}
    .close-btn{
      position:absolute;
      top:10px;right:15px;
      font-size:22px;
      cursor:pointer;
      color:#555;
    }
    .close-btn:hover{color:#000}

    @media(min-width:700px){
      .grid{flex-direction:row}
      aside{flex:1;position:sticky;top:120px;align-self:start;margin-left:15px}
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div style="width:60px;height:60px;border-radius:10px;background:linear-gradient(135deg,#0b63d6,#7bb3ff);display:flex;align-items:center;justify-content:center;color:#fff;font-weight:700;font-size:18px">CP</div>
      <div class="brand">
        <h1>Estacionamento Vertical Automatizado</h1>
        <div class="subtitle">Colégio Pentágono — Curso Técnico em Mecatrônica · 2025</div>
      </div>
    </header>

    <div class="menu">
      <a href="#" onclick="openModal('Elevador parado')">🚧 Elevador parado</a>
      <a href="#" onclick="openModal('Muito tempo de espera')">⏳ Muito tempo de espera</a>
      <a href="#" onclick="openModal('Informações gerais')">ℹ️ Informações</a>
      <a href="https://wa.me/5511958276139" target="_blank">💬 WhatsApp</a>
      <a class="emergencia" href="tel:190">🚔 Emergência Policial (190)</a>
      <a class="emergencia" href="tel:193">🚒 Emergência Bombeiros (193)</a>
      <a href="https://emersonvilela520-sudo.github.io/estacionamento-projeto/" target="_blank">🌐 Site</a>
      <a href="#" onclick="openModal('Reclamações')">📢 Reclamações</a>
    </div>

    <nav class="card" aria-label="Sumário">
      <strong>Sumário</strong>
      <a href="#introducao">1. Introdução</a>
      <a href="#objetivo">2. Objetivo</a>
      <a href="#desenvolvimento">3. Desenvolvimento</a>
      <a href="#resultados">4. Resultados</a>
      <a href="#conclusao">5. Conclusão</a>
      <a href="#referencias">6. Referências</a>
    </nav>

    <div class="grid">
      <main>
        <article class="card section" id="introducao">
          <h2>1. Introdução</h2>
          <p>O projeto teve início no primeiro semestre com a construção de um protótipo mecânico de elevação baseado em motor de vidro elétrico, fuso e guias lineares.</p>
          <p>No segundo semestre, foi integrado Arduino, ponte H e sensores de detecção, tornando o protótipo automatizado.</p>
          <img src="https://i.postimg.cc/w7L0X5KV/file-00000000d06061fb84b98df3e8702f32.png" alt="Protótipo" onclick="openImage(this.src)"/>
        </article>

        <article class="card section" id="objetivo">
          <h2>2. Objetivo</h2>
          <p>Desenvolver e implementar um protótipo de Estacionamento Vertical Automatizado, integrando soluções mecânicas e eletrônicas, oferecendo eficiência, segurança e experiência prática.</p>
        </article>

        <article class="card section" id="desenvolvimento">
          <h2>3. Desenvolvimento</h2>
          <section id="estrutura">
            <h3>3.1 Estrutura Mecânica</h3>
            <p>Sistema de elevação com motor de vidro elétrico, perfil de alumínio, acrílico, fuso de 8 mm, mancais e guias lineares.</p>
            <img src="https://i.postimg.cc/ppzqfQNf/IMG-20250912-WA0038.jpg" alt="Estrutura Mecânica" onclick="openImage(this.src)"/>
          </section>

          <section id="integracao">
            <h3>3.2 Integração Eletrônica</h3>
            <p>Automação com Arduino Uno, ponte H e sensores infravermelhos. Controle bidirecional do motor e paradas automáticas.</p>
            <img src="https://i.postimg.cc/nCB04K8G/IMG-20250912-WA0040.jpg" alt="Integração Eletrônica" onclick="openImage(this.src)"/>
            <img src="https://i.postimg.cc/xcMtvGrP/IMG-20250912-WA0041.jpg" alt="Componentes adicionais" onclick="openImage(this.src)"/>
          </section>

          <section id="desafios">
            <h3>3.3 Desafios Encontrados</h3>
            <p>Dificuldades na programação, alinhamento da maquete e restrição de tempo, exigindo desmontagens e substituições de componentes.</p>
            <img src="https://i.postimg.cc/MvVd70kt/IMG-20250912-WA0069.jpg" alt="Desafios" onclick="openImage(this.src)"/>
          </section>

          <section id="diagrama">
            <h3>3.4 Diagrama de Funcionamento</h3>
            <img src="https://i.postimg.cc/GHGqFP0P/Screenshot-20250916-095434-589.png" alt="Diagrama de Funcionamento" onclick="openImage(this.src)"/>
            <img src="https://i.postimg.cc/zVK0CwmS/Screenshot-20250924-225609-721.png" alt="Diagrama adicional" onclick="openImage(this.src)"/>
          </section>
        </article>

        <article class="card section" id="resultados">
          <h2>4. Resultados</h2>
          <p>O sistema apresentou movimentação vertical e transversal funcionais, paradas automáticas controladas por sensores IR e gerenciamento via Arduino.</p>
        </article>

        <article class="card section" id="conclusao">
          <h2>5. Conclusão</h2>
          <p>O projeto demonstrou a eficácia da integração entre mecânica, eletrônica e programação, evoluindo para um sistema automatizado realista.</p>
        </article>

        <article class="card section" id="referencias">
          <h2>6. Referências</h2>
          <ol>
            <li>BOLTON, W. Mecatrônica: sistemas de controle eletromecânico. 5.ed. São Paulo: Pearson, 2015.</li>
            <li>OGATA, Katsuhiko. Engenharia de Controle Moderno. 5.ed. São Paulo: Pearson, 2010.</li>
            <li>SUNFAR. Manual do Inversor de Frequência E550. Sunfar, 2023.</li>
            <li>Material e anotações das aulas do Curso Técnico em Mecatrônica – Colégio Pentágono, 2024-2025.</li>
          </ol>
        </article>
      </main>
    </div>

    <!-- Modal de suporte -->
    <div id="modal" class="modal">
      <div class="modal-content">
        <span class="close-btn" onclick="closeModal()">&times;</span>
        <h2 id="modal-title">Título</h2>
        <p id="modal-text">Conteúdo da informação.</p>
      </div>
    </div>

    <!-- Modal de imagens -->
    <div id="modal-img" class="modal" onclick="closeImage()">
      <div class="modal-content">
        <span class="close-btn" onclick="closeImage()">&times;</span>
        <img id="img-view" src="" alt="Imagem Ampliada"/>
      </div>
    </div>

    <footer>
      Criado automaticamente a partir do PDF fornecido — Colégio Pentágono · 2025
    </footer>
  </div>

  <script>
    // Modal de suporte
    function openModal(title){
      document.getElementById('modal-title').innerText = title;
      document.getElementById('modal-text').innerText = 'Aqui você pode adicionar detalhes sobre "' + title + '".';
      document.getElementById('modal').style.display = 'flex';
    }
    function closeModal(){document.getElementById('modal').style.display = 'none'}

    // Modal de imagens
    function openImage(src){
      document.getElementById('img-view').src = src;
      document.getElementById('modal-img').style.display = 'flex';
    }
    function closeImage(){
      document.getElementById('modal-img').style.display = 'none';
    }

    window.onclick = function(event){
      if(event.target.id == 'modal'){closeModal();}
      if(event.target.id == 'modal-img'){closeImage();}
    }
  </script>
</body>
</html>