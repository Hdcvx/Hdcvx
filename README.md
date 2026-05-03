<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vitor — AI Data Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0f1e;
    --surface: #111827;
    --surface2: #1a2236;
    --border: rgba(99, 179, 237, 0.15);
    --border2: rgba(99, 179, 237, 0.3);
    --accent: #63b3ed;
    --accent2: #4fd1c5;
    --accent3: #f6ad55;
    --text: #e2e8f0;
    --muted: #718096;
    --dim: #4a5568;
    --mono: 'Space Mono', monospace;
    --sans: 'DM Sans', sans-serif;
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    min-height: 100vh;
    padding: 48px 24px;
    background-image:
      radial-gradient(ellipse 80% 50% at 50% -20%, rgba(99,179,237,0.08) 0%, transparent 60%),
      radial-gradient(ellipse 40% 30% at 90% 80%, rgba(79,209,197,0.05) 0%, transparent 50%);
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
  }

  /* === HEADER === */
  .header {
    display: flex;
    align-items: flex-start;
    gap: 32px;
    margin-bottom: 48px;
    padding-bottom: 40px;
    border-bottom: 1px solid var(--border);
  }

  .avatar-wrap {
    flex-shrink: 0;
    position: relative;
  }

  .avatar {
    width: 88px;
    height: 88px;
    border-radius: 50%;
    background: linear-gradient(135deg, #1a2236 0%, #2d3748 100%);
    border: 2px solid var(--border2);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--mono);
    font-size: 28px;
    font-weight: 700;
    color: var(--accent);
    letter-spacing: -1px;
  }

  .status-dot {
    position: absolute;
    bottom: 4px;
    right: 4px;
    width: 14px;
    height: 14px;
    background: #48bb78;
    border-radius: 50%;
    border: 2px solid var(--bg);
  }

  .header-info { flex: 1; }

  .name {
    font-family: var(--mono);
    font-size: 28px;
    font-weight: 700;
    color: #fff;
    letter-spacing: -0.5px;
    margin-bottom: 6px;
  }

  .name span { color: var(--accent); }

  .headline {
    font-size: 14px;
    color: var(--accent2);
    font-family: var(--mono);
    margin-bottom: 12px;
    letter-spacing: 0.5px;
  }

  .desc {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.7;
    max-width: 560px;
  }

  .tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 16px;
  }

  .tag {
    font-family: var(--mono);
    font-size: 11px;
    padding: 3px 10px;
    border-radius: 3px;
    border: 1px solid var(--border2);
    color: var(--accent);
    background: rgba(99,179,237,0.06);
    letter-spacing: 0.3px;
  }

  .tag.green { color: var(--accent2); border-color: rgba(79,209,197,0.3); background: rgba(79,209,197,0.06); }
  .tag.amber { color: var(--accent3); border-color: rgba(246,173,85,0.3); background: rgba(246,173,85,0.06); }

  /* === SECTION === */
  .section { margin-bottom: 40px; }

  .section-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 2px;
    color: var(--dim);
    text-transform: uppercase;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* === STACK GRID === */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 12px;
  }

  .stack-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 16px;
    transition: border-color 0.2s, background 0.2s;
  }

  .stack-card:hover {
    border-color: var(--border2);
    background: var(--surface2);
  }

  .stack-card-label {
    font-size: 10px;
    font-family: var(--mono);
    color: var(--dim);
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  .stack-items {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .pill {
    font-size: 12px;
    font-family: var(--mono);
    padding: 3px 8px;
    border-radius: 4px;
    background: var(--surface2);
    color: var(--text);
    border: 1px solid var(--border);
  }

  .pill.blue { color: #90cdf4; background: rgba(144,205,244,0.08); border-color: rgba(144,205,244,0.2); }
  .pill.teal { color: #81e6d9; background: rgba(129,230,217,0.08); border-color: rgba(129,230,217,0.2); }
  .pill.amber { color: #fbd38d; background: rgba(251,211,141,0.08); border-color: rgba(251,211,141,0.2); }
  .pill.purple { color: #d6bcfa; background: rgba(214,188,250,0.08); border-color: rgba(214,188,250,0.2); }
  .pill.green { color: #9ae6b4; background: rgba(154,230,180,0.08); border-color: rgba(154,230,180,0.2); }
  .pill.coral { color: #fc8181; background: rgba(252,129,129,0.08); border-color: rgba(252,129,129,0.2); }

  /* === PROJECTS === */
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  @media (max-width: 600px) {
    .projects-grid { grid-template-columns: 1fr; }
    .header { flex-direction: column; gap: 16px; }
  }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 18px 20px;
    transition: border-color 0.2s;
    position: relative;
    overflow: hidden;
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
  }

  .project-card.blue::before { background: linear-gradient(90deg, #63b3ed, transparent); }
  .project-card.teal::before { background: linear-gradient(90deg, #4fd1c5, transparent); }
  .project-card.amber::before { background: linear-gradient(90deg, #f6ad55, transparent); }
  .project-card.purple::before { background: linear-gradient(90deg, #b794f4, transparent); }

  .project-card:hover { border-color: var(--border2); }

  .project-name {
    font-family: var(--mono);
    font-size: 13px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 6px;
  }

  .project-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.6;
    margin-bottom: 12px;
  }

  .project-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
  }

  .project-pill {
    font-size: 10px;
    font-family: var(--mono);
    padding: 2px 7px;
    border-radius: 3px;
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    color: var(--muted);
  }

  /* === FOCUS === */
  .focus-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }

  @media (max-width: 500px) { .focus-list { grid-template-columns: 1fr; } }

  .focus-item {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 16px;
  }

  .focus-icon {
    width: 32px;
    height: 32px;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 15px;
    flex-shrink: 0;
  }

  .fi-blue { background: rgba(99,179,237,0.1); }
  .fi-teal { background: rgba(79,209,197,0.1); }
  .fi-amber { background: rgba(246,173,85,0.1); }
  .fi-purple { background: rgba(183,148,244,0.1); }

  .focus-text-title {
    font-size: 13px;
    font-weight: 500;
    color: var(--text);
    margin-bottom: 2px;
  }

  .focus-text-sub {
    font-size: 12px;
    color: var(--muted);
    line-height: 1.5;
  }

  /* === STATS === */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 10px;
  }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 16px;
    text-align: center;
  }

  .stat-num {
    font-family: var(--mono);
    font-size: 22px;
    font-weight: 700;
    color: var(--accent);
    margin-bottom: 4px;
    line-height: 1;
  }

  .stat-label {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.5px;
  }

  /* === FOOTER === */
  .footer {
    margin-top: 48px;
    padding-top: 24px;
    border-top: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: gap;
    gap: 12px;
  }

  .footer-text {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--dim);
  }

  .footer-text span { color: var(--accent2); }

  .contact-row {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
  }

  .contact-link {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.2s;
  }

  .contact-link:hover { color: var(--accent); }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(16px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .header { animation: fadeUp 0.5s ease both; }
  .section:nth-child(2) { animation: fadeUp 0.5s 0.1s ease both; }
  .section:nth-child(3) { animation: fadeUp 0.5s 0.2s ease both; }
  .section:nth-child(4) { animation: fadeUp 0.5s 0.3s ease both; }
  .section:nth-child(5) { animation: fadeUp 0.5s 0.4s ease both; }
  .footer { animation: fadeUp 0.5s 0.5s ease both; }
</style>
</head>
<body>
<div class="container">

  <!-- HEADER -->
  <div class="header">
    <div class="avatar-wrap">
      <div class="avatar">V</div>
      <div class="status-dot"></div>
    </div>
    <div class="header-info">
      <div class="name">Vitor <span>_</span></div>
      <div class="headline">// AI Data Engineer · LLM Agents · Data Pipelines · Fintech</div>
      <div class="desc">
        Analista financeiro em transição para AI Data Engineering. Construindo pipelines de dados,
        sistemas multi-agentes com LLMs e aplicações fintech no cruzamento entre mercados e inteligência artificial.
        Baseado em Curitiba, BR.
      </div>
      <div class="tags">
        <span class="tag">📍 Curitiba, BR</span>
        <span class="tag green">🎓 Ciência de Dados &amp; ML — UniDomBosco</span>
        <span class="tag amber">⚡ Open to opportunities</span>
      </div>
    </div>
  </div>

  <!-- STACK -->
  <div class="section">
    <div class="section-label">stack técnica</div>
    <div class="stack-grid">

      <div class="stack-card">
        <div class="stack-card-label">AI Agents &amp; LLMs</div>
        <div class="stack-items">
          <span class="pill purple">CrewAI</span>
          <span class="pill purple">LangChain</span>
          <span class="pill purple">LlamaIndex</span>
          <span class="pill purple">MCP</span>
        </div>
      </div>

      <div class="stack-card">
        <div class="stack-card-label">Vector &amp; Storage</div>
        <div class="stack-items">
          <span class="pill teal">Qdrant</span>
          <span class="pill teal">PostgreSQL</span>
          <span class="pill teal">DuckDB</span>
          <span class="pill teal">Parquet</span>
        </div>
      </div>

      <div class="stack-card">
        <div class="stack-card-label">Data Engineering</div>
        <div class="stack-items">
          <span class="pill blue">PySpark</span>
          <span class="pill blue">Delta Lake</span>
          <span class="pill blue">Databricks</span>
          <span class="pill blue">dbt</span>
          <span class="pill blue">Prefect</span>
        </div>
      </div>

      <div class="stack-card">
        <div class="stack-card-label">Python &amp; Libs</div>
        <div class="stack-items">
          <span class="pill green">Python</span>
          <span class="pill green">Polars</span>
          <span class="pill green">Pandas</span>
          <span class="pill green">PyArrow</span>
          <span class="pill green">uv</span>
        </div>
      </div>

      <div class="stack-card">
        <div class="stack-card-label">Observability &amp; UI</div>
        <div class="stack-items">
          <span class="pill amber">LangFuse</span>
          <span class="pill amber">DeepEval</span>
          <span class="pill amber">Chainlit</span>
        </div>
      </div>

      <div class="stack-card">
        <div class="stack-card-label">Infra &amp; Cloud</div>
        <div class="stack-items">
          <span class="pill coral">Docker</span>
          <span class="pill coral">AWS S3</span>
          <span class="pill coral">FastAPI</span>
          <span class="pill coral">Git</span>
        </div>
      </div>

    </div>
  </div>

  <!-- PROJETOS -->
  <div class="section">
    <div class="section-label">projetos em destaque</div>
    <div class="projects-grid">

      <div class="project-card blue">
        <div class="project-name">duka_etl</div>
        <div class="project-desc">Pipeline ETL de tick data Dukascopy com Medallion Architecture (Bronze → Silver → Gold) em DuckDB e Parquet.</div>
        <div class="project-pills">
          <span class="project-pill">DuckDB</span>
          <span class="project-pill">Parquet</span>
          <span class="project-pill">PyArrow</span>
          <span class="project-pill">lzma</span>
          <span class="project-pill">Pandas</span>
        </div>
      </div>

      <div class="project-card teal">
        <div class="project-name">ICT Trading Agent</div>
        <div class="project-desc">Sistema multi-agente com CrewAI aplicando metodologia ICT/SMC para análise e geração de setups em EURUSD.</div>
        <div class="project-pills">
          <span class="project-pill">CrewAI</span>
          <span class="project-pill">ICT/SMC</span>
          <span class="project-pill">EURUSD</span>
          <span class="project-pill">Backtesting</span>
        </div>
      </div>

      <div class="project-card amber">
        <div class="project-name">duka_databricks</div>
        <div class="project-desc">Migração do pipeline Dukascopy para Databricks com PySpark + Delta Lake, CDC e orquestração na plataforma.</div>
        <div class="project-pills">
          <span class="project-pill">Databricks</span>
          <span class="project-pill">PySpark</span>
          <span class="project-pill">Delta Lake</span>
          <span class="project-pill">AWS S3</span>
        </div>
      </div>

      <div class="project-card purple">
        <div class="project-name">FinAgent FII</div>
        <div class="project-desc">Agente de análise de FIIs com RAG + CrewAI seguindo padrão: ingestão → Postgres/Qdrant → agentes → Chainlit.</div>
        <div class="project-pills">
          <span class="project-pill">CrewAI</span>
          <span class="project-pill">Qdrant</span>
          <span class="project-pill">LangFuse</span>
          <span class="project-pill">Chainlit</span>
          <span class="project-pill">MCP</span>
        </div>
      </div>

    </div>
  </div>

  <!-- FOCO ATUAL -->
  <div class="section">
    <div class="section-label">foco atual</div>
    <div class="focus-list">

      <div class="focus-item">
        <div class="focus-icon fi-blue">📊</div>
        <div>
          <div class="focus-text-title">Backtesting Forex Platform</div>
          <div class="focus-text-sub">MVP com DuckDB/Parquet + engine Python. Próximas fases: métricas Sharpe/drawdown, frontend Next.js e AI Strategy Builder.</div>
        </div>
      </div>

      <div class="focus-item">
        <div class="focus-icon fi-teal">🤖</div>
        <div>
          <div class="focus-text-title">Personal Trading Copilot</div>
          <div class="focus-text-sub">RAG + agentes sobre metodologia ICT/SMC própria, vetorizada no Qdrant para suporte às operações.</div>
        </div>
      </div>

      <div class="focus-item">
        <div class="focus-icon fi-amber">🏗️</div>
        <div>
          <div class="focus-text-title">Databricks &amp; Delta Lake</div>
          <div class="focus-text-sub">Aprofundamento em Spark + Delta com foco em certificação Databricks Data Engineer Associate.</div>
        </div>
      </div>

      <div class="focus-item">
        <div class="focus-icon fi-purple">🌐</div>
        <div>
          <div class="focus-text-title">Posicionamento Internacional</div>
          <div class="focus-text-sub">Inglês técnico, GitHub público e portfolio direcionado a fintechs e consultorias de dados globais.</div>
        </div>
      </div>

    </div>
  </div>

  <!-- STATS -->
  <div class="section">
    <div class="section-label">em números</div>
    <div class="stats-row">
      <div class="stat-card">
        <div class="stat-num">3+</div>
        <div class="stat-label">projetos portfolio</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">4</div>
        <div class="stat-label">agentes CrewAI</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">3</div>
        <div class="stat-label">camadas medallion</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">2029</div>
        <div class="stat-label">conclusão graduação</div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-text">
      built with <span>curiosidade</span> · Curitiba, BR · 2025
    </div>
    <div class="contact-row">
      <a href="#" class="contact-link">linkedin</a>
      <a href="#" class="contact-link">github</a>
      <a href="#" class="contact-link">email</a>
    </div>
  </div>

</div>
</body>
</html>
