<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Aleksandr Gordeev — Data Analyst Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg:          #0d1117;
    --surface:     #161b22;
    --surface2:    #1c2230;
    --border:      rgba(255,255,255,0.07);
    --border-hover:rgba(255,255,255,0.15);
    --accent:      #4f8ef7;
    --accent2:     #38d9a9;
    --accent3:     #f5a623;
    --text:        #e6edf3;
    --muted:       #8b949e;
    --serif:       'DM Serif Display', Georgia, serif;
    --sans:        'DM Sans', system-ui, sans-serif;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    font-weight: 300;
    line-height: 1.7;
    min-height: 100vh;
    overflow-x: hidden;
  }

  body::before {
    content: '';
    position: fixed; inset: 0; z-index: 0;
    background:
      radial-gradient(ellipse 80% 60% at 10% 0%, rgba(79,142,247,0.12) 0%, transparent 60%),
      radial-gradient(ellipse 60% 50% at 90% 100%, rgba(56,217,169,0.09) 0%, transparent 55%),
      radial-gradient(ellipse 50% 40% at 50% 50%, rgba(245,166,35,0.04) 0%, transparent 60%);
    pointer-events: none;
  }

  body::after {
    content: '';
    position: fixed; inset: 0; z-index: 0;
    background-image:
      linear-gradient(rgba(255,255,255,0.015) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.015) 1px, transparent 1px);
    background-size: 48px 48px;
    pointer-events: none;
  }

  .wrap {
    position: relative; z-index: 1;
    max-width: 800px;
    margin: 0 auto;
    padding: 3rem 1.5rem 5rem;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .fade { animation: fadeUp 0.6s ease both; }
  .fade:nth-child(1) { animation-delay: 0.05s; }
  .fade:nth-child(2) { animation-delay: 0.15s; }
  .fade:nth-child(3) { animation-delay: 0.25s; }
  .fade:nth-child(4) { animation-delay: 0.35s; }
  .fade:nth-child(5) { animation-delay: 0.45s; }

  /* ── Header ── */
  .header {
    display: flex; align-items: center; gap: 1.5rem;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 2rem 2.25rem;
    margin-bottom: 2rem;
    position: relative; overflow: hidden;
  }
  .header::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2), var(--accent3));
  }
  .avatar {
    width: 126px; height: 126px; border-radius: 50%;
    border: 2px solid rgba(79,142,247,0.4);
    object-fit: cover; flex-shrink: 0;
  }
  .avatar-fallback {
    width: 126px; height: 126px; border-radius: 50%;
    background: linear-gradient(135deg, #1a3a6e, #0f2a52);
    border: 2px solid rgba(79,142,247,0.4);
    display: none; align-items: center; justify-content: center;
    font-family: var(--serif); font-size: 24px; color: #90b8f8;
    flex-shrink: 0;
  }
  .header-text h1 {
    font-family: var(--serif); font-size: 26px; font-weight: 400;
    letter-spacing: -0.3px; margin-bottom: 4px;
  }
  .header-text .role { font-size: 14px; color: var(--muted); margin-bottom: 10px; }
  .badges { display: flex; flex-wrap: wrap; gap: 6px; }
  .badge {
    font-size: 11px; font-weight: 500; padding: 3px 10px;
    border-radius: 99px;
    border: 1px solid rgba(79,142,247,0.35);
    background: rgba(79,142,247,0.1);
    color: #90b8f8;
  }
  .badge.green {
    border-color: rgba(56,217,169,0.35);
    background: rgba(56,217,169,0.1);
    color: #72e8c8;
  }

  /* ── Section label ── */
  .section-label {
    font-size: 11px; font-weight: 500; letter-spacing: 0.1em;
    text-transform: uppercase; color: var(--muted);
    display: flex; align-items: center; gap: 10px;
    margin-bottom: 1rem;
  }
  .section-label::after { content: ''; flex: 1; height: 1px; background: var(--border); }

  /* ── About ── */
  .about-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.5rem 1.75rem;
    margin-bottom: 2rem;
    font-size: 14.5px; color: var(--muted); line-height: 1.8;
  }
  .about-card strong { color: var(--text); font-weight: 500; }
  .stack-wrap { margin-top: 1.25rem; display: flex; flex-wrap: wrap; gap: 7px; }
  .skill-tag {
    font-size: 12px; font-weight: 400; padding: 4px 12px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: var(--surface2);
    color: var(--muted);
    transition: border-color 0.2s, color 0.2s;
  }
  .skill-tag:hover { border-color: var(--border-hover); color: var(--text); }

  /* ── Project cards ── */
  .projects { display: flex; flex-direction: column; gap: 12px; margin-bottom: 2rem; }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
    transition: border-color 0.2s;
  }
  .project-card:hover { border-color: var(--border-hover); }

  .project-trigger {
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.1rem 1.5rem; cursor: pointer;
    user-select: none; gap: 1rem;
  }
  .project-left { display: flex; align-items: center; gap: 14px; }

  .p-icon {
    width: 38px; height: 38px; border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 17px; flex-shrink: 0;
  }
  .p-icon.blue  { background: rgba(79,142,247,0.12); border: 1px solid rgba(79,142,247,0.2); }
  .p-icon.teal  { background: rgba(56,217,169,0.10); border: 1px solid rgba(56,217,169,0.2); }
  .p-icon.amber { background: rgba(245,166,35,0.10); border: 1px solid rgba(245,166,35,0.2); }

  .p-name { font-size: 14px; font-weight: 500; color: var(--text); }
  .p-meta { font-size: 12px; color: var(--muted); margin-top: 2px; }

  .p-arrow {
    width: 24px; height: 24px; border-radius: 50%;
    background: var(--surface2); border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0; transition: background 0.2s, transform 0.3s;
    font-size: 10px; color: var(--muted);
  }
  .project-card.open .p-arrow { transform: rotate(180deg); background: rgba(79,142,247,0.12); color: var(--accent); }

  .project-body {
    max-height: 0; overflow: hidden;
    transition: max-height 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .project-body-inner {
    border-top: 1px solid var(--border);
    padding: 1.25rem 1.5rem 1.5rem;
  }

  .p-desc { font-size: 13.5px; color: var(--muted); line-height: 1.75; margin-bottom: 1rem; }

  /* ── Project images ── */
  .img-grid { display: grid; gap: 10px; margin: 1rem 0; }
  .img-grid.cols-2 { grid-template-columns: 1fr 1fr; }
  .img-grid.cols-1 { grid-template-columns: 1fr; }

  .img-grid img {
    width: 100%; border-radius: 10px;
    border: 1px solid var(--border);
    object-fit: cover; display: block;
    transition: border-color 0.2s, transform 0.25s;
  }
  .img-grid img:hover { border-color: var(--border-hover); transform: scale(1.015); }

  .img-label {
    font-size: 11px; color: var(--muted); text-align: center;
    margin-top: 5px; margin-bottom: 8px; letter-spacing: 0.04em;
  }

  .outcomes-title {
    font-size: 11px; font-weight: 500; letter-spacing: 0.08em;
    text-transform: uppercase; color: var(--muted);
    margin: 1rem 0 0.6rem;
  }
  .outcomes { list-style: none; display: flex; flex-direction: column; gap: 8px; }
  .outcomes li {
    font-size: 13px; color: var(--muted); line-height: 1.65;
    padding-left: 14px;
    border-left: 2px solid rgba(79,142,247,0.3);
  }
  .outcomes li strong { color: var(--text); font-weight: 500; }

  .tools-row { display: flex; flex-wrap: wrap; gap: 5px; margin-top: 1rem; }
  .tool {
    font-size: 11px; padding: 3px 9px; border-radius: 6px;
    background: var(--surface2); border: 1px solid var(--border); color: var(--muted);
  }

  /* ── Contact ── */
  .contact-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.5rem 1.75rem;
    display: flex; flex-wrap: wrap; gap: 1.5rem;
  }
  .contact-item { display: flex; align-items: center; gap: 10px; }
  .c-dot {
    width: 32px; height: 32px; border-radius: 50%;
    background: var(--surface2); border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    font-size: 13px; color: var(--muted);
  }
  .c-label { font-size: 11px; color: var(--muted); }
  .c-val { font-size: 13px; font-weight: 500; color: var(--text); }
  .c-val a { color: var(--accent); text-decoration: none; }
  .c-val a:hover { text-decoration: underline; }

  @media (max-width: 540px) {
    .header { flex-direction: column; text-align: center; }
    .badges { justify-content: center; }
    .contact-card { flex-direction: column; }
    .img-grid.cols-2 { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>
<div class="wrap">

  <!-- Header -->
  <div class="header fade">
    <img
      class="avatar"
      src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/linkedin_profile_pic.jpeg"
      alt="Aleksandr Gordeev"
      onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';"
    />
    <div class="avatar-fallback">AG</div>
    <div class="header-text">
      <h1>Aleksandr Gordeev</h1>
      <p class="role">Data Analyst &nbsp;·&nbsp; Business Analyst</p>
      <div class="badges">
        <span class="badge">MSc Business Analytics — Distinction</span>
        <span class="badge green">Open to opportunities</span>
      </div>
    </div>
  </div>

  <!-- About -->
  <div class="section-label fade">About</div>
  <div class="about-card fade">
    Data Analyst with a <strong>Distinction in MSc Business Analytics</strong> and a strong foundation in market research and data-driven strategic decision-making. Experienced in <strong>ETL, data cleaning &amp; preparation</strong>, structured analysis, and translating complex data into actionable insights through clear storytelling. Skilled at bridging technical findings with business strategy to drive growth.
    <div class="stack-wrap">
      <span class="skill-tag">Python</span>
      <span class="skill-tag">Power BI</span>
      <span class="skill-tag">SQL</span>
      <span class="skill-tag">Machine Learning</span>
      <span class="skill-tag">LLM</span>
      <span class="skill-tag">Statistical Analysis</span>
      <span class="skill-tag">Hypothesis Testing</span>
      <span class="skill-tag">Market Research</span>
      <span class="skill-tag">Go-to-Market</span>
      <span class="skill-tag">Advanced Excel</span>
    </div>
  </div>

  <!-- Projects -->
  <div class="section-label fade">Projects</div>
  <div class="projects fade">

    <!-- Project 1: Loan Analysis -->
    <div class="project-card" id="p1">
      <div class="project-trigger" onclick="toggle('p1')">
        <div class="project-left">
          <div class="p-icon blue">📊</div>
          <div>
            <div class="p-name">Loan Analysis — Power BI Dashboard</div>
            <div class="p-meta">Portfolio risk · Customer segmentation · Profitability KPIs</div>
          </div>
        </div>
        <div class="p-arrow">▼</div>
      </div>
      <div class="project-body" id="p1-body">
        <div class="project-body-inner">
          <p class="p-desc">Analysed a lending portfolio to identify growth opportunities and risk control improvements, delivering an interactive Power BI dashboard for strategic decision-making.</p>

          <div class="img-grid cols-1">
            <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/Dashboard_Snapshot.png" alt="Dashboard Overview" />
          </div>
          <p class="img-label">Dashboard overview</p>

          <div class="img-grid cols-2">
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/Customer_Segmentation.png" alt="Customer Segmentation" />
              <p class="img-label">Customer segmentation</p>
            </div>
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/Profit_Analysis.png" alt="Profit Analysis" />
              <p class="img-label">Profit analysis</p>
            </div>
          </div>

          <div class="img-grid cols-1">
            <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/Risk_Analysis.png" alt="Risk Analysis" />
          </div>
          <p class="img-label">Risk analysis</p>

          <div class="outcomes-title">Key outcomes</div>
          <ul class="outcomes">
            <li>Identified most profitable states and customer groups by income band and loan purpose — wedding loans showed a <strong>17.6% higher profit margin</strong> than the overall portfolio.</li>
            <li>Uncovered grade-C loans as the best risk-adjusted return opportunity — <strong>7.11% return</strong> while representing only 27.9% of the portfolio, highlighting scalable growth potential.</li>
            <li>Deployed interactive dashboard integrating Portfolio at Risk, Loan YoY growth, weighted interest rate, and profitability KPIs for data-driven risk and lending strategy.</li>
          </ul>
          <div class="tools-row">
            <span class="tool">Power BI</span><span class="tool">DAX</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Project 2: British Airways -->
    <div class="project-card" id="p2">
      <div class="project-trigger" onclick="toggle('p2')">
        <div class="project-left">
          <div class="p-icon teal">✈️</div>
          <div>
            <div class="p-name">British Airways — NLP &amp; Predictive Modelling</div>
            <div class="p-meta">Sentiment analysis · Random Forest · Booking prediction</div>
          </div>
        </div>
        <div class="p-arrow">▼</div>
      </div>
      <div class="project-body" id="p2-body">
        <div class="project-body-inner">
          <p class="p-desc">End-to-end NLP and machine learning pipeline analysing British Airways customer reviews and predicting booking completion to support marketing and customer experience strategy.</p>

          <div class="img-grid cols-2">
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/BA_sentiiment_table.png" alt="Sentiment Table" />
              <p class="img-label">Sentiment table</p>
            </div>
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/BA_sentiment_distribution.png" alt="Sentiment Distribution" />
              <p class="img-label">Sentiment distribution</p>
            </div>
          </div>

          <div class="img-grid cols-1">
            <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/BA_features_viz.png" alt="Feature Importance" />
          </div>
          <p class="img-label">Predictive model — feature importance</p>

          <div class="outcomes-title">Key outcomes</div>
          <ul class="outcomes">
            <li>Scraped and processed third-party review data with BeautifulSoup &amp; NLTK, mapping satisfaction distribution across positive, neutral, and negative segments using VADER sentiment.</li>
            <li>Built a Random Forest classifier achieving <strong>85.44% accuracy</strong> in predicting booking completion — identifying destination, purchase lead, and flight length as key behavioural drivers.</li>
            <li>Delivered visualised insights structured for non-technical stakeholder communication.</li>
          </ul>
          <div class="tools-row">
            <span class="tool">Python</span><span class="tool">BeautifulSoup</span><span class="tool">NLTK</span>
            <span class="tool">VADER Sentiment</span><span class="tool">Scikit-learn</span><span class="tool">Pandas</span><span class="tool">Matplotlib</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Project 3: Fraud Detection -->
    <div class="project-card" id="p3">
      <div class="project-trigger" onclick="toggle('p3')">
        <div class="project-left">
          <div class="p-icon amber">💳</div>
          <div>
            <div class="p-name">Credit Card Fraud Detection — 1.85M Records</div>
            <div class="p-meta">Geospatial analysis · Customer segmentation · Fraud patterns</div>
          </div>
        </div>
        <div class="p-arrow">▼</div>
      </div>
      <div class="project-body" id="p3-body">
        <div class="project-body-inner">
          <p class="p-desc">Analysed a large credit card transaction dataset of <strong>1.85 million records</strong> including transaction timestamps, amounts, merchant details, customer demographics, and geospatial information to surface fraud risk areas and customer behaviour trends.</p>

          <div class="img-grid cols-2">
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_segm_age.png" alt="Segmentation by Age" />
              <p class="img-label">Segmentation by age</p>
            </div>
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_spent_age.png" alt="Spending by Age" />
              <p class="img-label">Spending by age</p>
            </div>
          </div>

          <div class="img-grid cols-1">
            <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_segm_category.png" alt="Segmentation by Category" />
          </div>
          <p class="img-label">Segmentation by purchase category</p>

          <div class="img-grid cols-1">
            <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_avgspent_category.png" alt="Avg Spend by Category" />
          </div>
          <p class="img-label">Average spend by category</p>

          <div class="img-grid cols-2">
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_totamount_byjob.png" alt="Total Spend by Job" />
              <p class="img-label">Total spend by job title</p>
            </div>
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_jobs_avgspent.png" alt="Avg Spend by Job" />
              <p class="img-label">Avg spend by job role</p>
            </div>
          </div>

          <div class="img-grid cols-1">
            <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_trans_map.png" alt="Transaction Map" />
          </div>
          <p class="img-label">Transaction volume by US state</p>

          <div class="img-grid cols-1">
            <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_fraud_map.png" alt="Fraud Map" />
          </div>
          <p class="img-label">Fraud transaction volume by location</p>

          <div class="img-grid cols-2">
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_fraud_merchants.png" alt="Top Fraud Merchants" />
              <p class="img-label">Top fraud merchants</p>
            </div>
            <div>
              <img src="https://raw.githubusercontent.com/AlexGordeev1661/AlexGordeev1661.github.io/main/images/FD_fraud_names.png" alt="Top Fraud Customers" />
              <p class="img-label">Top fraud customers</p>
            </div>
          </div>

          <div class="outcomes-title">Key outcomes</div>
          <ul class="outcomes">
            <li>Identified business growth opportunities through complex customer segmentation by age group, job role, and purchase category — revealing key spending behaviour patterns.</li>
            <li>Mapped transaction geographic distribution across US states, identifying high-risk fraud regions and the merchants and customers with the highest fraudulent transaction counts.</li>
          </ul>
          <div class="tools-row">
            <span class="tool">Python</span><span class="tool">Pandas</span><span class="tool">NumPy</span>
            <span class="tool">Matplotlib</span><span class="tool">Seaborn</span><span class="tool">Geospatial Analysis</span>
          </div>
        </div>
      </div>
    </div>

  </div>

  <!-- Contact -->
  <div class="section-label fade">Contact</div>
  <div class="contact-card fade">
    <div class="contact-item">
      <div class="c-dot">in</div>
      <div>
        <div class="c-label">LinkedIn</div>
        <div class="c-val"><a href="https://www.linkedin.com/in/aleksandr99gordeev/" target="_blank">Aleksandr Gordeev</a></div>
      </div>
    </div>
    <div class="contact-item">
      <div class="c-dot">@</div>
      <div>
        <div class="c-label">Email</div>
        <div class="c-val"><a href="mailto:contact.alexgordeev@gmail.com">contact.alexgordeev@gmail.com</a></div>
      </div>
    </div>
    <div class="contact-item">
      <div class="c-dot">☎</div>
      <div>
        <div class="c-label">Phone</div>
        <div class="c-val">+44 7521 469593</div>
      </div>
    </div>
  </div>

</div>

<script>
function toggle(id) {
  const card = document.getElementById(id);
  const body = document.getElementById(id + '-body');
  const isOpen = card.classList.contains('open');
  card.classList.toggle('open', !isOpen);
  body.style.maxHeight = isOpen ? '0' : body.scrollHeight + 'px';
}
</script>
</body>
</html>
