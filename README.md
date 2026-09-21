<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#166534">
  <meta name="description" content="AgroFácil - Sistema leve de apoio e gestão para a avicultura familiar.">
  <title>AgroFácil | Gestão da Avicultura Familiar</title>

  <style>
    :root {
      --primary: #166534;
      --primary-2: #15803d;
      --primary-3: #22c55e;
      --bg: #f4f7f2;
      --card: #ffffff;
      --text: #172018;
      --muted: #647067;
      --border: #dbe5dc;
      --danger: #b91c1c;
      --warning: #a16207;
      --shadow: 0 12px 30px rgba(22, 101, 52, 0.08);
      --radius: 18px;
    }

    [data-theme="dark"] {
      --bg: #0f1712;
      --card: #16221a;
      --text: #f0fdf4;
      --muted: #a3b8a8;
      --border: #283a2d;
      --shadow: 0 12px 30px rgba(0, 0, 0, 0.3);
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      font-family: Arial, Helvetica, sans-serif;
      color: var(--text);
      background: var(--bg);
      line-height: 1.6;
      transition: background 0.3s, color 0.3s;
    }

    button, input, select, textarea { font: inherit; }
    a { color: inherit; text-decoration: none; }

    .container {
      width: min(1120px, 92%);
      margin: 0 auto;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 20;
      background: rgba(255,255,255,0.96);
      border-bottom: 1px solid var(--border);
      backdrop-filter: blur(8px);
    }

    [data-theme="dark"] header {
      background: rgba(22, 34, 26, 0.96);
    }

    .nav {
      min-height: 72px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 15px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 800;
      color: var(--primary);
      font-size: 1.25rem;
    }

    [data-theme="dark"] .brand { color: var(--primary-3); }

    .brand-icon {
      width: 40px;
      height: 40px;
      display: grid;
      place-items: center;
      border-radius: 12px;
      color: white;
      background: linear-gradient(135deg, var(--primary), var(--primary-3));
    }

    .nav-right {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .nav-links {
      display: flex;
      gap: 6px;
      flex-wrap: wrap;
    }

    .nav-links a {
      padding: 8px 12px;
      border-radius: 10px;
      color: var(--muted);
      font-weight: 600;
      font-size: .92rem;
    }

    .nav-links a:hover, .nav-links a:focus {
      background: rgba(34, 197, 94, 0.15);
      color: var(--primary-3);
    }

    .theme-toggle {
      background: transparent;
      border: 1px solid var(--border);
      padding: 7px 11px;
      border-radius: 10px;
      cursor: pointer;
      color: var(--text);
      font-size: 0.9rem;
    }

    .hero {
      padding: 60px 0 40px;
      background: radial-gradient(circle at 90% 10%, rgba(34,197,94,.15), transparent 30%);
    }

    .hero-grid {
      display: grid;
      grid-template-columns: 1.2fr .8fr;
      gap: 35px;
      align-items: center;
    }

    .eyebrow {
      color: var(--primary-3);
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: .08em;
      font-size: .78rem;
      margin-bottom: 10px;
    }

    h1 {
      font-size: clamp(2rem, 4.5vw, 3.5rem);
      line-height: 1.1;
      margin-bottom: 18px;
    }

    .hero p {
      color: var(--muted);
      max-width: 650px;
      font-size: 1.05rem;
      margin-bottom: 25px;
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
    }

    .btn {
      border: 0;
      border-radius: 12px;
      padding: 12px 18px;
      font-weight: 700;
      cursor: pointer;
      transition: .2s ease;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }

    .btn:hover { transform: translateY(-1px); }

    .btn-primary { background: var(--primary); color: white; }
    .btn-primary:hover { background: var(--primary-2); }

    .btn-secondary { background: var(--card); color: var(--text); border: 1px solid var(--border); }
    .btn-secondary:hover { background: rgba(0,0,0,0.03); }

    .btn-danger { background: #fee2e2; color: var(--danger); }
    [data-theme="dark"] .btn-danger { background: #450a0a; color: #fca5a5; }

    .btn-small { padding: 8px 12px; font-size: .85rem; }

    .hero-card {
      background: linear-gradient(145deg, #14532d, #166534);
      color: white;
      padding: 26px;
      border-radius: 24px;
      box-shadow: var(--shadow);
    }

    .hero-card h2 { margin-bottom: 10px; }
    .hero-card p { color: #e9f8ec; font-size: .95rem; margin-bottom: 18px; }

    .mini-stats {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 12px;
    }

    .mini-stat {
      padding: 14px;
      border: 1px solid rgba(255,255,255,.15);
      background: rgba(255,255,255,.08);
      border-radius: 14px;
    }

    .mini-stat strong { display: block; font-size: 1.3rem; }
    .mini-stat span { font-size: .82rem; color: #d7f4dc; }

    section { padding: 50px 0; }

    .section-title {
      text-align: center;
      max-width: 760px;
      margin: 0 auto 28px;
    }

    .section-title h2 {
      font-size: clamp(1.6rem, 3vw, 2.3rem);
      margin-bottom: 8px;
    }

    .section-title p { color: var(--muted); }

    .grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
    .grid-2 { display: grid; grid-template-columns: repeat(2, 1fr); gap: 18px; }

    .card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 22px;
      box-shadow: var(--shadow);
    }

    .card h3 { margin-bottom: 8px; }
    .card p { color: var(--muted); }

    .icon-box {
      width: 44px;
      height: 44px;
      border-radius: 13px;
      display: grid;
      place-items: center;
      background: rgba(34, 197, 94, 0.12);
      margin-bottom: 14px;
      font-size: 1.3rem;
    }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 14px;
    }

    .field { display: flex; flex-direction: column; gap: 6px; }
    .field.full { grid-column: 1 / -1; }

    label { font-weight: 700; font-size: .9rem; }

    input, select, textarea {
      width: 100%;
      border: 1px solid var(--border);
      border-radius: 11px;
      padding: 10px 12px;
      background: var(--card);
      color: var(--text);
    }

    input:focus, select:focus, textarea:focus {
      outline: 2px solid var(--primary-3);
    }

    textarea { min-height: 100px; resize: vertical; }

    .actions { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 15px; }

    .result {
      margin-top: 17px;
      padding: 15px;
      border-radius: 12px;
      background: rgba(34, 197, 94, 0.1);
      border: 1px solid var(--primary-3);
    }

    .result strong { display: block; font-size: 1.1rem; }

    .table-wrap { overflow-x: auto; margin-top: 18px; }

    table {
      width: 100%;
      border-collapse: collapse;
      min-width: 500px;
    }

    th, td {
      padding: 10px;
      border-bottom: 1px solid var(--border);
      text-align: left;
    }

    th { background: rgba(0, 0, 0, 0.03); }

    .empty { text-align: center; color: var(--muted); padding: 20px; }

    .accordion {
      border: 1px solid var(--border);
      border-radius: 12px;
      margin-bottom: 10px;
      overflow: hidden;
    }

    .accordion-header {
      width: 100%;
      background: var(--card);
      padding: 14px;
      text-align: left;
      font-weight: 700;
      border: 0;
      cursor: pointer;
      display: flex;
      justify-content: space-between;
      color: var(--text);
    }

    .accordion-body {
      padding: 14px;
      background: rgba(0,0,0,0.02);
      border-top: 1px solid var(--border);
      display: none;
      color: var(--muted);
    }

    .accordion.open .accordion-body { display: block; }

    .stats {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 12px;
      margin-top: 18px;
    }

    .stat-card {
      padding: 15px;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 14px;
    }

    .stat-card span { display: block; color: var(--muted); font-size: .8rem; }
    .stat-card strong { font-size: 1.3rem; }

    footer {
      background: #0d1a12;
      color: #dbe9de;
      padding: 30px 0;
      margin-top: 40px;
      font-size: .9rem;
    }

    .toast {
      position: fixed;
      right: 18px;
      bottom: 18px;
      z-index: 50;
      padding: 12px 18px;
      border-radius: 12px;
      background: #102218;
      color: white;
      box-shadow: 0 12px 35px rgba(0,0,0,.3);
      max-width: min(360px, 90vw);
      opacity: 0;
      transform: translateY(15px);
      pointer-events: none;
      transition: .25s ease;
    }

    .toast.show { opacity: 1; transform: translateY(0); }
    .hidden { display: none !important; }

    @media (max-width: 860px) {
      .hero-grid, .grid-3, .grid-2 { grid-template-columns: 1fr; }
      .stats { grid-template-columns: repeat(2, 1fr); }
      .nav { flex-direction: column; align-items: flex-start; padding: 12px 0; }
      .nav-right { width: 100%; justify-content: space-between; }
      .nav-links { overflow-x: auto; flex-wrap: nowrap; width: 100%; padding-bottom: 5px; }
    }
  </style>
</head>

<body>
  <header>
    <div class="container nav">
      <a class="brand" href="#inicio" onclick="registrarAcesso('Início')">
        <span class="brand-icon">🌱</span>
        <span>AgroFácil</span>
      </a>

      <div class="nav-right">
        <nav class="nav-links">
          <a href="#inicio" onclick="registrarAcesso('Início')">Início</a>
          <a href="#ferramentas" onclick="registrarAcesso('Ferramentas')">Ferramentas</a>
          <a href="#diario" onclick="registrarAcesso('Diário')">Diário</a>
          <a href="#financeiro" onclick="registrarAcesso('Financeiro')">Financeiro</a>
          <a href="#cartilhas" onclick="registrarAcesso('Cartilhas')">Cartilhas</a>
          <a href="#logs" onclick="registrarAcesso('Logs')">Acessos</a>
          <a href="#feedback" onclick="registrarAcesso('Feedback')">Feedback</a>
        </nav>
        <button class="theme-toggle" onclick="alternarTema()" id="btnTema">🌙</button>
      </div>
    </div>
  </header>

  <main>
    <section class="hero" id="inicio">
      <div class="container hero-grid">
        <div>
          <div class="eyebrow">Tecnologia para a agricultura familiar</div>
          <h1>Gestão simples para uma criação mais organizada.</h1>
          <p>
            O AgroFácil reúne calculadoras de alimentação e água, diário de manejo,
            anotador financeiro, cartilhas de orientação e histórico de acessos.
          </p>

          <div class="hero-actions">
            <a class="btn btn-primary" href="#ferramentas" onclick="registrarAcesso('Ferramentas')">Começar agora</a>
            <a class="btn btn-secondary" href="#diario" onclick="registrarAcesso('Diário')">Abrir diário</a>
          </div>
        </div>

        <aside class="hero-card">
          <h2>Controle em um só lugar</h2>
          <p>Registros salvos e armazenados no próprio dispositivo para facilitar o acompanhamento local.</p>

          <div class="mini-stats">
            <div class="mini-stat">
              <strong id="hero-registros">0</strong>
              <span>registros no diário</span>
            </div>
            <div class="mini-stat">
              <strong id="hero-acessos">0</strong>
              <span>acessos gravados</span>
            </div>
          </div>
        </aside>
      </div>
    </section>

    <section id="ferramentas">
      <div class="container">
        <div class="section-title">
          <h2>Ferramentas principais</h2>
          <p>Preencha os dados abaixo e obtenha as estimativas exatas para o seu lote.</p>
        </div>

        <div class="grid-2">
          <div class="card">
            <div class="icon-box">🌾</div>
            <h3>Calculadora de ração</h3>
            <p>Estime o total de ração necessário para o lote no período desejado.</p>

            <div class="form-grid" style="margin-top:16px">
              <div class="field full">
                <label for="tipoAveRacao">Perfil/Tipo de Ave</label>
                <select id="tipoAveRacao" onchange="atualizarPerfilRacao()">
                  <option value="custom">Personalizado</option>
                  <option value="caipira" selected>Caipira / Pé-Duro (100g/dia)</option>
                  <option value="postura">Galinha de Postura (120g/dia)</option>
                  <option value="corte">Frango de Corte (150g/dia)</option>
                </select>
              </div>

              <div class="field">
                <label for="aves">Nº de Aves</label>
                <input id="aves" type="number" min="1" placeholder="Ex.: 50">
              </div>

              <div class="field">
                <label for="racaoAve">Consumo (g/ave/dia)</label>
                <input id="racaoAve" type="number" min="1" value="100">
              </div>

              <div class="field full">
                <label for="diasRacao">Período (dias)</label>
                <input id="diasRacao" type="number" min="1" value="30">
              </div>
            </div>

            <div class="actions">
              <button class="btn btn-primary" onclick="calcularRacao()">Calcular Ração</button>
            </div>

            <div id="resultadoRacao" class="result hidden"></div>
          </div>

          <div class="card">
            <div class="icon-box">💧</div>
            <h3>Calculadora de água</h3>
            <p>Estime o volume total de água limpa para o consumo das aves.</p>

            <div class="form-grid" style="margin-top:16px">
              <div class="field">
                <label for="aguaAves">Nº de Aves</label>
                <input id="aguaAves" type="number" min="1" placeholder="Ex.: 50">
              </div>

              <div class="field">
                <label for="aguaAve">Consumo (ml/ave/dia)</label>
                <input id="aguaAve" type="number" min="1" value="250">
              </div>

              <div class="field full">
                <label for="diasAgua">Período (dias)</label>
                <input id="diasAgua" type="number" min="1" value="1">
              </div>
            </div>

            <div class="actions">
              <button class="btn btn-primary" onclick="calcularAgua()">Calcular Água</button>
            </div>

            <div id="resultadoAgua" class="result hidden"></div>
          </div>
        </div>
      </div>
    </section>

    <section id="diario">
      <div class="container">
        <div class="section-title">
          <h2>Diário de manejo</h2>
          <p>Anote ocorrências sanitárias, vacinação, mortandade e postura de ovos.</p>
        </div>

        <div class="card">
          <div class="form-grid">
            <div class="field">
              <label for="dataRegistro">Data</label>
              <input id="dataRegistro" type="date">
            </div>

            <div class="field">
              <label for="tipoRegistro">Categoria</label>
              <select id="tipoRegistro">
                <option>Alimentação</option>
                <option>Saúde</option>
                <option>Produção</option>
                <option>Manejo</option>
                <option>Observação</option>
              </select>
            </div>

            <div class="field full">
              <label for="tituloRegistro">Título do ocorrido</label>
              <input id="tituloRegistro" type="text" placeholder="Ex.: Aplicação de medicação / Coleta de Ovos">
            </div>

            <div class="field full">
              <label for="descricaoRegistro">Descrição/Detalhes</label>
              <textarea id="descricaoRegistro" placeholder="Descreva observações, doses aplicadas ou sintomas observados..."></textarea>
            </div>
          </div>

          <div class="actions">
            <button class="btn btn-primary" onclick="salvarRegistro()">Salvar no Diário</button>
            <button class="btn btn-secondary" onclick="exportarDados()">Exportar Backup (JSON)</button>
            <button class="btn btn-danger" onclick="limparRegistros()">Limpar Diário</button>
          </div>

          <div class="stats">
            <div class="stat-card"><span>Total Registros</span><strong id="statTotal">0</strong></div>
            <div class="stat-card"><span>Produção</span><strong id="statProducao">0</strong></div>
            <div class="stat-card"><span>Saúde</span><strong id="statSaude">0</strong></div>
            <div class="stat-card"><span>Observações</span><strong id="statObservacao">0</strong></div>
          </div>

          <div class="table-wrap">
            <table>
              <thead>
                <tr>
                  <th>Data</th>
                  <th>Tipo</th>
                  <th>Título</th>
                  <th>Descrição</th>
                  <th>Ação</th>
                </tr>
              </thead>
              <tbody id="tabelaRegistros"></tbody>
            </table>
          </div>
        </div>
      </div>
    </section>

    <!-- SEÇÃO FINANCEIRA ATUALIZADA COM O ANOTADOR DE GASTOS -->
    <section id="financeiro">
      <div class="container">
        <div class="section-title">
          <h2>Simulador e Anotador Financeiro</h2>
          <p>Anote as suas despesas e receitas para apurar o lucro ou prejuízo do lote.</p>
        </div>

        <div class="grid-2">
          <!-- Coluna 1: Registrador de Gastos e Vendas -->
          <div class="card">
            <h3>1. Registrar Gastos / Despesas</h3>
            <p style="font-size: 0.85rem; color: var(--muted); margin-bottom: 12px;">
              Ex.: Compra de milho, remédios, vacinas ou transporte.
            </p>
            
            <div class="form-grid">
              <div class="field">
                <label for="descGasto">Descrição do Gasto</label>
                <input id="descGasto" type="text" placeholder="Ex.: Milho, Remédio">
              </div>

              <div class="field">
                <label for="valorGasto">Valor (R$)</label>
                <input id="valorGasto" type="number" step="0.01" min="0" placeholder="Ex.: 50.00">
              </div>
            </div>

            <div class="actions">
              <button class="btn btn-secondary btn-small" onclick="adicionarGasto()">+ Adicionar Gasto</button>
            </div>

            <!-- Tabela Dinâmica de Gastos -->
            <div class="table-wrap" style="margin-top: 15px;">
              <table>
                <thead>
                  <tr>
                    <th>Item</th>
                    <th>Valor</th>
                    <th>Ação</th>
                  </tr>
                </thead>
                <tbody id="tabelaGastos">
                  <tr><td colspan="3" class="empty">Nenhum gasto adicionado.</td></tr>
                </tbody>
              </table>
            </div>

            <hr style="margin: 20px 0; border: 0; border-top: 1px solid var(--border);">

            <h3>2. Registrar Vendas (Receita)</h3>
            <div class="form-grid" style="margin-top:10px;">
              <div class="field">
                <label for="quantidadeVenda">Qtd. Vendida</label>
                <input id="quantidadeVenda" type="number" min="0" placeholder="Ex.: 80 (ovos/aves)">
              </div>

              <div class="field">
                <label for="precoVenda">Preço Unitário (R$)</label>
                <input id="precoVenda" type="number" step="0.01" min="0" placeholder="Ex.: 25.00">
              </div>
            </div>

            <div class="actions" style="margin-top: 15px;">
              <button class="btn btn-primary" onclick="calcularFinanceiroCompleto()">Calcular Saldo Final</button>
            </div>

            <!-- Resultado com Destaque Verde (Lucro) ou Vermelho (Prejuízo) -->
            <div id="resultadoFinanceiro" class="result hidden" style="margin-top: 20px;"></div>
          </div>

          <!-- Coluna 2: Dicas e orientações -->
          <div class="card">
            <h3>Dicas de Controle Financeiro</h3>
            <p style="margin-top:10px;">Para garantir o lucro da produção familiar:</p>
            <ul style="margin-left:20px; margin-top:10px; color:var(--muted)">
              <li>Registre todos os pequenos gastos (como remédios e sacos de milho) para não perder o controle do lote.</li>
              <li>Sempre que fizer uma venda, insira a quantidade e o valor cobrado.</li>
              <li>Acompanhe o saldo: se o resultado ficar em <span style="color:var(--danger); font-weight:bold;">vermelho</span>, significa que as vendas não cobriram os custos acumulados.</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <section id="cartilhas">
      <div class="container">
        <div class="section-title">
          <h2>Cartilhas e orientações de manejo</h2>
          <p>Guias práticos para garantir a saúde e a produtividade da criação.</p>
        </div>

        <div class="accordion">
          <button class="accordion-header" onclick="toggleAccordion(this)">
            <span>🌾 Formulação e Mistura Caseira de Ração (Milho e Soja)</span>
            <span>▼</span>
          </button>
          <div class="accordion-body">
            <p>Para aves caipiras, uma mistura equilibrada contém 60% de milho moído, 25% de farelo de soja, 10% de núcleo mineral/calcário e 5% de restos vegetais higienizados. Varie a mistura conforme a fase (crescimento vs. postura).</p>
          </div>
        </div>

        <div class="accordion">
          <button class="accordion-header" onclick="toggleAccordion(this)">
            <span>🐔 Prevenção da Coccidiose e Doenças Sanitárias</span>
            <span>▼</span>
          </button>
          <div class="accordion-body">
            <p>Mantenha a cama do galinheiro sempre seca. Cama úmida é o ambiente ideal para a multiplicação de parasitas. Utilize chá de folha de goiabeira como adstringente caseiro inicial em casos leves de diarreia e isole a ave doente.</p>
          </div>
        </div>

        <div class="accordion">
          <button class="accordion-header" onclick="toggleAccordion(this)">
            <span>💡 Iluminação e Estímulo para Postura de Ovos</span>
            <span>▼</span>
          </button>
          <div class="accordion-body">
            <p>Galinhas necessitam de 14 a 16 horas de luz diária para manter a produção constante de ovos. Em épocas de dias mais curtos, utilize lâmpadas LED econômicas no galinheiro por 2 horas ao amanhecer ou ao anoitecer.</p>
          </div>
        </div>
      </div>
    </section>

    <section id="logs">
      <div class="container">
        <div class="section-title">
          <h2>Relatório de acessos e interações (Logs)</h2>
          <p>Registro local gerado automaticamente para comprovação de testes e aplicação do sistema.</p>
        </div>

        <div class="card">
          <div class="actions" style="margin-bottom:15px;">
            <button class="btn btn-secondary btn-small" onclick="renderizarLogs()">Atualizar Tabela</button>
            <button class="btn btn-danger btn-small" onclick="limparLogs()">Apagar Histórico de Logs</button>
          </div>

          <div class="table-wrap">
            <table>
              <thead>
                <tr>
                  <th>Data/Hora</th>
                  <th>Identificador/Usuário</th>
                  <th>Aba / Seção Acessada</th>
                </tr>
              </thead>
              <tbody id="tabelaLogs"></tbody>
            </table>
          </div>
        </div>
      </div>
    </section>

    <section id="feedback">
      <div class="container">
        <div class="section-title">
          <h2>Feedback da comunidade</h2>
          <p>Envie sua avaliação para apoiar a melhoria contínua da ferramenta AgroFácil.</p>
        </div>

        <div class="grid-2">
          <div class="card">
            <div class="field">
              <label for="nomeFeedback">Seu Nome / Produtor Rural</label>
              <input id="nomeFeedback" type="text" placeholder="Ex.: João da Silva (Comunidade Santana)">
            </div>

            <div class="field" style="margin-top:13px">
              <label for="notaFeedback">Avaliação do Sistema</label>
              <select id="notaFeedback">
                <option value="5">5 - Excelente (Fácil e muito útil)</option>
                <option value="4">4 - Muito bom</option>
                <option value="3">3 - Satisfatório / Bom</option>
                <option value="2">2 - Regular</option>
                <option value="1">1 - Difícil de usar</option>
              </select>
            </div>

            <div class="field" style="margin-top:13px">
              <label for="comentarioFeedback">Sugestão ou Opinião</label>
              <textarea id="comentarioFeedback" placeholder="Conte como o site te ajudou ou o que podemos melhorar..."></textarea>
            </div>

            <div class="actions">
              <button class="btn btn-primary" onclick="salvarFeedback()">Enviar Avaliação</button>
            </div>
          </div>

          <div class="card">
            <h3>Avaliações Registradas</h3>
            <div id="listaFeedbacks" style="margin-top:12px"></div>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <div class="container" style="text-align:center;">
      <h3>AgroFácil | Projeto de Extensão Universitária</h3>
      <p style="margin-top:6px;">Desenvolvido por Geovane Rocha Boa Sorte para apoio à Avicultura Familiar.</p>
      <p style="margin-top:4px; opacity:0.7;">Todos os dados são armazenados localmente e respeitam a privacidade do usuário.</p>
    </div>
  </footer>

  <div id="toast" class="toast"></div>

  <script>
    const STORAGE_REGISTROS = "agrofacil_registros_v4";
    const STORAGE_FEEDBACK = "agrofacil_feedback_v4";
    const STORAGE_LOGS = "agrofacil_logs_v4";
    const STORAGE_GASTOS = "agrofacil_gastos_v4";

    let registros = carregar(STORAGE_REGISTROS);
    let feedbacks = carregar(STORAGE_FEEDBACK);
    let logs = carregar(STORAGE_LOGS);
    let listaGastos = carregar(STORAGE_GASTOS);

    function carregar(chave) {
      try {
        const dados = localStorage.getItem(chave);
        return dados ? JSON.parse(dados) : [];
      } catch (e) {
        return [];
      }
    }

    function salvarLocal(chave, dados) {
      localStorage.setItem(chave, JSON.stringify(dados));
    }

    function registrarAcesso(secao) {
      const novoLog = {
        dataHora: new Date().toLocaleString("pt-BR"),
        usuario: document.getElementById("nomeFeedback").value.trim() || "Produtor Local / Visitante",
        secao
      };
      logs.unshift(novoLog);
      logs = logs.slice(0, 30);
      salvarLocal(STORAGE_LOGS, logs);
      renderizarLogs();
    }

    function renderizarLogs() {
      const tabela = document.getElementById("tabelaLogs");
      if (!logs.length) {
        tabela.innerHTML = `<tr><td colspan="3" class="empty">Nenhum log registrado ainda.</td></tr>`;
      } else {
        tabela.innerHTML = logs.map(log => `
          <tr>
            <td>${log.dataHora}</td>
            <td>${escaparHTML(log.usuario)}</td>
            <td>${escaparHTML(log.secao)}</td>
          </tr>
        `).join("");
      }
      document.getElementById("hero-acessos").textContent = logs.length;
    }

    function limparLogs() {
      logs = [];
      salvarLocal(STORAGE_LOGS, logs);
      renderizarLogs();
      mostrarToast("Histórico de logs limpo.");
    }

    function alternarTema() {
      const body = document.body;
      const btn = document.getElementById("btnTema");
      if (body.getAttribute("data-theme") === "dark") {
        body.removeAttribute("data-theme");
        btn.textContent = "🌙";
      } else {
        body.setAttribute("data-theme", "dark");
        btn.textContent = "☀️";
      }
    }

    function toggleAccordion(btn) {
      const item = btn.parentElement;
      item.classList.toggle("open");
    }

    function mostrarToast(msg) {
      const toast = document.getElementById("toast");
      toast.textContent = msg;
      toast.classList.add("show");
      clearTimeout(window.toastTimer);
      window.toastTimer = setTimeout(() => toast.classList.remove("show"), 2800);
    }

    function atualizarPerfilRacao() {
      const tipo = document.getElementById("tipoAveRacao").value;
      const inputConsumo = document.getElementById("racaoAve");
      if (tipo === "caipira") inputConsumo.value = 100;
      if (tipo === "postura") inputConsumo.value = 120;
      if (tipo === "corte") inputConsumo.value = 150;
    }

    function calcularRacao() {
      const aves = Number(document.getElementById("aves").value);
      const racaoAve = Number(document.getElementById("racaoAve").value);
      const dias = Number(document.getElementById("diasRacao").value);

      if (!aves || !racaoAve || !dias || aves <= 0 || racaoAve <= 0 || dias <= 0) {
        mostrarToast("Preencha os dados da ração corretamente.");
        return;
      }

      const totalKg = (aves * racaoAve * dias) / 1000;
      const res = document.getElementById("resultadoRacao");
      res.classList.remove("hidden");
      res.innerHTML = `
        <strong>Total Necessário: ${totalKg.toFixed(2)} kg de ração</strong>
        Consumo médio estimado de ${((aves * racaoAve) / 1000).toFixed(2)} kg por dia para ${aves} aves.
      `;
      registrarAcesso("Calculadora de Ração (Cálculo Efetuado)");
    }

    function calcularAgua() {
      const aves = Number(document.getElementById("aguaAves").value);
      const aguaAve = Number(document.getElementById("aguaAve").value);
      const dias = Number(document.getElementById("diasAgua").value);

      if (!aves || !aguaAve || !dias || aves <= 0 || aguaAve <= 0 || dias <= 0) {
        mostrarToast("Preencha os dados de água corretamente.");
        return;
      }

      const totalLitros = (aves * aguaAve * dias) / 1000;
      const res = document.getElementById("resultadoAgua");
      res.classList.remove("hidden");
      res.innerHTML = `
        <strong>Total Necessário: ${totalLitros.toFixed(2)} Litros de água</strong>
        Consumo diário de ${((aves * aguaAve) / 1000).toFixed(2)} Litros para ${aves} aves.
      `;
      registrarAcesso("Calculadora de Água (Cálculo Efetuado)");
    }

    function salvarRegistro() {
      const data = document.getElementById("dataRegistro").value;
      const tipo = document.getElementById("tipoRegistro").value;
      const titulo = document.getElementById("tituloRegistro").value.trim();
      const descricao = document.getElementById("descricaoRegistro").value.trim();

      if (!data || !titulo || !descricao) {
        mostrarToast("Preencha data, título e descrição.");
        return;
      }

      registros.unshift({
        id: String(Date.now()),
        data, tipo, titulo, descricao
      });

      salvarLocal(STORAGE_REGISTROS, registros);
      document.getElementById("tituloRegistro").value = "";
      document.getElementById("descricaoRegistro").value = "";
      renderizarRegistros();
      mostrarToast("Novo registro salvo no diário!");
      registrarAcesso("Diário de Manejo (Novo Registro)");
    }

    function excluirRegistro(id) {
      registros = registros.filter(r => r.id !== id);
      salvarLocal(STORAGE_REGISTROS, registros);
      renderizarRegistros();
      mostrarToast("Registro excluído.");
    }

    function limparRegistros() {
      if (!registros.length) return mostrarToast("O diário já está vazio.");
      if (confirm("Deseja apagar todos os registros do diário?")) {
        registros = [];
        salvarLocal(STORAGE_REGISTROS, registros);
        renderizarRegistros();
        mostrarToast("Diário limpo.");
      }
    }

    function renderizarRegistros() {
      const tabela = document.getElementById("tabelaRegistros");
      if (!registros.length) {
        tabela.innerHTML = `<tr><td colspan="5" class="empty">Nenhum registro no diário.</td></tr>`;
      } else {
        tabela.innerHTML = registros.map(r => `
          <tr>
            <td>${r.data.split("-").reverse().join("/")}</td>
            <td>${escaparHTML(r.tipo)}</td>
            <td>${escaparHTML(r.titulo)}</td>
            <td>${escaparHTML(r.descricao)}</td>
            <td><button class="btn btn-danger btn-small" onclick="excluirRegistro('${r.id}')">Excluir</button></td>
          </tr>
        `).join("");
      }

      document.getElementById("statTotal").textContent = registros.length;
      document.getElementById("statProducao").textContent = registros.filter(r => r.tipo === "Produção").length;
      document.getElementById("statSaude").textContent = registros.filter(r => r.tipo === "Saúde").length;
      document.getElementById("statObservacao").textContent = registros.filter(r => r.tipo === "Observação").length;
      document.getElementById("hero-registros").textContent = registros.length;
    }

    /* LÓGICA DO ANOTADOR E SIMULADOR FINANCEIRO */
    function adicionarGasto() {
      const descInput = document.getElementById("descGasto");
      const valorInput = document.getElementById("valorGasto");

      const descricao = descInput.value.trim();
      const valor = Number(valorInput.value);

      if (!descricao || isNaN(valor) || valor <= 0) {
        mostrarToast("Preencha a descrição e um valor válido para o gasto.");
        return;
      }

      listaGastos.push({
        id: String(Date.now()),
        descricao,
        valor
      });

      salvarLocal(STORAGE_GASTOS, listaGastos);
      descInput.value = "";
      valorInput.value = "";

      renderizarTabelaGastos();
      mostrarToast("Gasto adicionado!");
      registrarAcesso("Anotador Financeiro (Gasto Adicionado)");
    }

    function removerGasto(id) {
      listaGastos = listaGastos.filter(item => item.id !== id);
      salvarLocal(STORAGE_GASTOS, listaGastos);
      renderizarTabelaGastos();
      mostrarToast("Gasto removido.");
    }

    function renderizarTabelaGastos() {
      const tabela = document.getElementById("tabelaGastos");
      if (!listaGastos.length) {
        tabela.innerHTML = `<tr><td colspan="3" class="empty">Nenhum gasto adicionado.</td></tr>`;
        return;
      }

      tabela.innerHTML = listaGastos.map(item => `
        <tr>
          <td>${escaparHTML(item.descricao)}</td>
          <td>${item.valor.toLocaleString("pt-BR", { style: "currency", currency: "BRL" })}</td>
          <td>
            <button class="btn btn-danger btn-small" onclick="removerGasto('${item.id}')">Excluir</button>
          </td>
        </tr>
      `).join("");
    }

    function calcularFinanceiroCompleto() {
      const qtd = Number(document.getElementById("quantidadeVenda").value) || 0;
      const preco = Number(document.getElementById("precoVenda").value) || 0;

      const totalCustos = listaGastos.reduce((acc, item) => acc + item.valor, 0);
      const receitaBruta = qtd * preco;
      const saldoFinal = receitaBruta - totalCustos;

      const res = document.getElementById("resultadoFinanceiro");
      res.classList.remove("hidden");

      if (saldoFinal < 0) {
        // Destaque em Vermelho em caso de Prejuízo
        res.style.backgroundColor = "#fef2f2";
        res.style.borderColor = "#ef4444";
        res.innerHTML = `
          <strong style="color: #b91c1c; font-size: 1.2rem;">
            ⚠️ SALDO FINAL: PREJUÍZO DE ${saldoFinal.toLocaleString("pt-BR", { style: "currency", currency: "BRL" })}
          </strong>
          <div style="margin-top: 6px; color: #7f1d1d; font-size: 0.95rem;">
            Receita Total: ${receitaBruta.toLocaleString("pt-BR", { style: "currency", currency: "BRL" })} | 
            Custos Totais: ${totalCustos.toLocaleString("pt-BR", { style: "currency", currency: "BRL" })}
          </div>
        `;
      } else {
        // Destaque em Verde em caso de Lucro
        res.style.backgroundColor = "rgba(34, 197, 94, 0.1)";
        res.style.borderColor = "var(--primary-3)";
        res.innerHTML = `
          <strong style="color: var(--primary-3); font-size: 1.2rem;">
            ✅ SALDO FINAL: LUCRO DE ${saldoFinal.toLocaleString("pt-BR", { style: "currency", currency: "BRL" })}
          </strong>
          <div style="margin-top: 6px; color: var(--text); font-size: 0.95rem;">
            Receita Total: ${receitaBruta.toLocaleString("pt-BR", { style: "currency", currency: "BRL" })} | 
            Custos Totais: ${totalCustos.toLocaleString("pt-BR", { style: "currency", currency: "BRL" })}
          </div>
        `;
      }

      registrarAcesso("Simulador Financeiro (Cálculo Efetuado)");
    }

    function exportarDados() {
      const payload = { projeto: "AgroFácil", registros, feedbacks, logs, listaGastos };
      const blob = new Blob([JSON.stringify(payload, null, 2)], { type: "application/json" });
      const a = document.createElement("a");
      a.href = URL.createObjectURL(blob);
      a.download = "agrofacil-backup.json";
      a.click();
      mostrarToast("Backup exportado em arquivo JSON!");
    }

    function salvarFeedback() {
      const nome = document.getElementById("nomeFeedback").value.trim() || "Produtor Anônimo";
      const nota = document.getElementById("notaFeedback").value;
      const comentario = document.getElementById("comentarioFeedback").value.trim();

      if (!comentario) return mostrarToast("Escreva seu comentário.");

      feedbacks.unshift({ nome, nota, comentario });
      feedbacks = feedbacks.slice(0, 10);
      salvarLocal(STORAGE_FEEDBACK, feedbacks);

      document.getElementById("comentarioFeedback").value = "";
      renderizarFeedbacks();
      mostrarToast("Feedback enviado com sucesso!");
      registrarAcesso("Feedback (Enviado)");
    }

    function renderizarFeedbacks() {
      const lista = document.getElementById("listaFeedbacks");
      if (!feedbacks.length) {
        lista.innerHTML = '<p class="empty">Nenhum feedback registrado.</p>';
        return;
      }
      lista.innerHTML = feedbacks.map(f => `
        <div style="padding:10px 0; border-bottom:1px solid var(--border)">
          <strong>${escaparHTML(f.nome)}</strong>
          <div style="font-size:.85rem; color:var(--primary-3)">Nota: ${"★".repeat(f.nota)}</div>
          <p style="font-size:.9rem;">${escaparHTML(f.comentario)}</p>
        </div>
      `).join("");
    }

    function escaparHTML(str) {
      return String(str).replace(/[&<>"']/g, m => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#039;' }[m]));
    }

    document.addEventListener("DOMContentLoaded", () => {
      document.getElementById("dataRegistro").valueAsDate = new Date();
      renderizarRegistros();
      renderizarFeedbacks();
      renderizarLogs();
      renderizarTabelaGastos();
      registrarAcesso("Acesso Inicial ao Site");
    });
  </script>
</body>
</html>
