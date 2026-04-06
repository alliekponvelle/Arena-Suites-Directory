<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🏟️ Arena Suites Directory</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
  /* ── Reset & Base ── */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bubble1: #ff85a1;
    --bubble2: #ffb347;
    --bubble3: #a0e7e5;
    --bubble4: #b8f0ae;
    --bubble5: #c9b1ff;
    --bubble6: #ffd6ec;
    --bg: #fff8fd;
    --card-bg: #ffffff;
    --text: #3d2c5e;
    --text2: #6b5b8a;
    --shadow: 0 8px 32px rgba(160,100,200,.13);
    --radius: 22px;
    --radius-sm: 14px;
  }

  body {
    font-family: 'Nunito', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── Animated Background Bubbles ── */
  .bg-bubbles {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 0;
    overflow: hidden;
  }
  .bg-bubbles span {
    position: absolute;
    border-radius: 50%;
    opacity: .13;
    animation: floatUp linear infinite;
  }
  .bg-bubbles span:nth-child(1)  { width:80px;  height:80px;  left:10%; background:var(--bubble1); animation-duration:12s; animation-delay:0s; }
  .bg-bubbles span:nth-child(2)  { width:60px;  height:60px;  left:25%; background:var(--bubble2); animation-duration:9s;  animation-delay:2s; }
  .bg-bubbles span:nth-child(3)  { width:100px; height:100px; left:40%; background:var(--bubble3); animation-duration:14s; animation-delay:4s; }
  .bg-bubbles span:nth-child(4)  { width:50px;  height:50px;  left:55%; background:var(--bubble5); animation-duration:10s; animation-delay:1s; }
  .bg-bubbles span:nth-child(5)  { width:70px;  height:70px;  left:70%; background:var(--bubble4); animation-duration:11s; animation-delay:3s; }
  .bg-bubbles span:nth-child(6)  { width:90px;  height:90px;  left:85%; background:var(--bubble1); animation-duration:13s; animation-delay:5s; }
  .bg-bubbles span:nth-child(7)  { width:55px;  height:55px;  left:5%;  background:var(--bubble5); animation-duration:8s;  animation-delay:6s; }
  .bg-bubbles span:nth-child(8)  { width:75px;  height:75px;  left:93%; background:var(--bubble2); animation-duration:15s; animation-delay:0s; }
  @keyframes floatUp {
    0%   { transform: translateY(110vh) scale(1); }
    100% { transform: translateY(-10vh) scale(1.1); }
  }

  /* ── Hero Header ── */
  .hero {
    position: relative;
    z-index: 1;
    text-align: center;
    padding: 54px 24px 36px;
    background: linear-gradient(135deg, #ffd6ec 0%, #d4c8ff 50%, #a0e7e5 100%);
    border-radius: 0 0 50px 50px;
    box-shadow: 0 10px 40px rgba(160,100,200,.18);
  }
  .hero-emoji { font-size: 3.6rem; display: block; animation: bounce 2s ease-in-out infinite; }
  @keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50%       { transform: translateY(-12px); }
  }
  .hero h1 {
    font-size: 2.8rem;
    font-weight: 900;
    color: #3d2c5e;
    letter-spacing: -0.5px;
    margin-top: 8px;
    line-height: 1.15;
  }
  .hero h1 span { color: var(--bubble1); }
  .hero p {
    font-size: 1.1rem;
    font-weight: 600;
    color: #6b5b8a;
    margin-top: 10px;
    max-width: 560px;
    margin-left: auto;
    margin-right: auto;
  }

  /* ── Search Bar ── */
  .search-wrap {
    position: relative;
    z-index: 1;
    max-width: 560px;
    margin: 28px auto 0;
    padding: 0 20px;
  }
  .search-wrap input {
    width: 100%;
    padding: 16px 22px 16px 54px;
    border: 3px solid #e8d5f5;
    border-radius: 50px;
    font-family: 'Nunito', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    color: var(--text);
    background: #fff;
    outline: none;
    transition: border .2s, box-shadow .2s;
    box-shadow: 0 4px 20px rgba(160,100,200,.10);
  }
  .search-wrap input::placeholder { color: #c4aee0; font-weight: 600; }
  .search-wrap input:focus { border-color: var(--bubble5); box-shadow: 0 4px 24px rgba(160,100,200,.22); }
  .search-icon {
    position: absolute;
    left: 38px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 1.3rem;
    pointer-events: none;
  }

  /* ── Tab Nav ── */
  .tabs {
    position: relative;
    z-index: 1;
    display: flex;
    justify-content: center;
    gap: 12px;
    padding: 28px 20px 8px;
    flex-wrap: wrap;
  }
  .tab-btn {
    padding: 12px 26px;
    border-radius: 50px;
    border: 3px solid transparent;
    font-family: 'Nunito', sans-serif;
    font-size: .95rem;
    font-weight: 800;
    cursor: pointer;
    transition: all .22s;
    background: #fff;
    color: var(--text2);
    box-shadow: 0 4px 14px rgba(0,0,0,.07);
  }
  .tab-btn:hover { transform: translateY(-3px); box-shadow: 0 8px 22px rgba(0,0,0,.12); }
  .tab-btn.active { color: #fff; border-color: transparent; transform: translateY(-3px); }
  .tab-btn[data-tab="resell"].active  { background: linear-gradient(135deg, var(--bubble1), #ff5580); }
  .tab-btn[data-tab="nba"].active     { background: linear-gradient(135deg, var(--bubble5), #7e22ce); }
  .tab-btn[data-tab="nfl"].active     { background: linear-gradient(135deg, var(--bubble2), #e85d04); }
  .tab-btn[data-tab="s101"].active    { background: linear-gradient(135deg, var(--bubble3), #0891b2); }

  /* ── Main Content ── */
  .main { position: relative; z-index: 1; padding: 24px 20px 60px; max-width: 1200px; margin: 0 auto; }

  /* ── Section ── */
  .section { display: none; }
  .section.active { display: block; }

  .section-title {
    text-align: center;
    font-size: 1.7rem;
    font-weight: 900;
    color: var(--text);
    margin-bottom: 24px;
  }
  .section-title span { display: inline-block; animation: wiggle 1.4s ease-in-out infinite; }
  @keyframes wiggle {
    0%, 100% { transform: rotate(-4deg); }
    50%       { transform: rotate(4deg); }
  }

  /* ── Resell Grid ── */
  .resell-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 18px;
    max-width: 900px;
    margin: 0 auto;
  }
  .resell-card {
    background: #fff;
    border-radius: var(--radius);
    padding: 28px 20px;
    text-align: center;
    box-shadow: var(--shadow);
    transition: transform .22s, box-shadow .22s;
    cursor: pointer;
    text-decoration: none;
    color: var(--text);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 12px;
    border: 3px solid transparent;
  }
  .resell-card:hover { transform: translateY(-8px) scale(1.03); box-shadow: 0 16px 48px rgba(160,100,200,.22); }
  .resell-card:nth-child(1) { border-color: #ff85a1; }
  .resell-card:nth-child(2) { border-color: #ffb347; }
  .resell-card:nth-child(3) { border-color: #a0e7e5; }
  .resell-card:nth-child(4) { border-color: #b8f0ae; }
  .resell-card:nth-child(5) { border-color: #c9b1ff; }
  .resell-card:nth-child(6) { border-color: #ffd6ec; }
  .resell-emoji { font-size: 2.4rem; }
  .resell-name { font-size: 1.05rem; font-weight: 800; color: var(--text); }
  .resell-url { font-size: .82rem; font-weight: 600; color: var(--text2); }
  .resell-badge {
    font-size: .72rem;
    font-weight: 800;
    padding: 4px 12px;
    border-radius: 50px;
    background: linear-gradient(135deg, #ffd6ec, #d4c8ff);
    color: var(--text);
  }

  /* ── Venue Grid ── */
  .venue-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
  }
  .venue-card {
    background: var(--card-bg);
    border-radius: var(--radius);
    padding: 24px;
    box-shadow: var(--shadow);
    transition: transform .22s, box-shadow .22s;
    border-top: 5px solid;
    position: relative;
    overflow: hidden;
  }
  .venue-card::before {
    content: '';
    position: absolute;
    top: -30px; right: -30px;
    width: 80px; height: 80px;
    border-radius: 50%;
    opacity: .08;
  }
  .venue-card:hover { transform: translateY(-6px); box-shadow: 0 18px 48px rgba(160,100,200,.20); }

  /* NBA card colors cycle */
  .nba-card:nth-child(4n+1) { border-color: var(--bubble1); }
  .nba-card:nth-child(4n+1)::before { background: var(--bubble1); }
  .nba-card:nth-child(4n+2) { border-color: var(--bubble5); }
  .nba-card:nth-child(4n+2)::before { background: var(--bubble5); }
  .nba-card:nth-child(4n+3) { border-color: var(--bubble3); }
  .nba-card:nth-child(4n+3)::before { background: var(--bubble3); }
  .nba-card:nth-child(4n+4) { border-color: var(--bubble2); }
  .nba-card:nth-child(4n+4)::before { background: var(--bubble2); }

  /* NFL card colors cycle */
  .nfl-card:nth-child(4n+1) { border-color: #ffb347; }
  .nfl-card:nth-child(4n+1)::before { background: #ffb347; }
  .nfl-card:nth-child(4n+2) { border-color: #b8f0ae; }
  .nfl-card:nth-child(4n+2)::before { background: #b8f0ae; }
  .nfl-card:nth-child(4n+3) { border-color: #a0e7e5; }
  .nfl-card:nth-child(4n+3)::before { background: #a0e7e5; }
  .nfl-card:nth-child(4n+4) { border-color: #ffd6ec; }
  .nfl-card:nth-child(4n+4)::before { background: #ffd6ec; }

  .venue-number {
    font-size: .78rem;
    font-weight: 800;
    color: #fff;
    background: var(--text2);
    width: 26px; height: 26px;
    border-radius: 50%;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 8px;
  }
  .venue-name {
    font-size: 1.12rem;
    font-weight: 900;
    color: var(--text);
    line-height: 1.25;
    margin-bottom: 4px;
  }
  .venue-team {
    font-size: .87rem;
    font-weight: 700;
    color: var(--text2);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 5px;
  }
  .venue-divider {
    border: none;
    border-top: 2px dashed #f0e8ff;
    margin-bottom: 14px;
  }
  .venue-info-row {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    margin-bottom: 10px;
    font-size: .88rem;
    font-weight: 700;
    color: var(--text);
    line-height: 1.4;
  }
  .venue-info-row .ico { font-size: 1.1rem; flex-shrink: 0; margin-top: 1px; }
  .venue-info-row a {
    color: var(--text);
    text-decoration: none;
    word-break: break-all;
    transition: color .18s;
  }
  .venue-info-row a:hover { color: var(--bubble1); text-decoration: underline; }

  .copy-btn {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    margin-top: 14px;
    padding: 8px 18px;
    border-radius: 50px;
    border: none;
    background: linear-gradient(135deg, #f3e8ff, #fce7f3);
    font-family: 'Nunito', sans-serif;
    font-size: .8rem;
    font-weight: 800;
    color: var(--text);
    cursor: pointer;
    transition: all .2s;
  }
  .copy-btn:hover { background: linear-gradient(135deg, #e9d5ff, #fbcfe8); transform: scale(1.05); }
  .copy-btn.copied { background: linear-gradient(135deg, #bbf7d0, #a7f3d0); }

  /* ── Info Banner ── */
  .info-banner {
    background: linear-gradient(135deg, #fde8ff 0%, #e0f2fe 100%);
    border-radius: var(--radius);
    padding: 22px 26px;
    margin-bottom: 28px;
    border: 2px solid #e9d5ff;
    text-align: center;
  }
  .info-banner p { font-size: .95rem; font-weight: 700; color: var(--text2); line-height: 1.6; }
  .info-banner strong { color: var(--text); }

  /* ── No Results ── */
  .no-results {
    text-align: center;
    padding: 60px 20px;
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--text2);
    display: none;
  }
  .no-results.show { display: block; }

  /* ── Count Badge ── */
  .count-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-size: .85rem;
    font-weight: 800;
    color: var(--text2);
    background: #f3e8ff;
    padding: 6px 16px;
    border-radius: 50px;
    margin: 0 auto 22px;
    width: fit-content;
    display: flex;
  }

  /* ── Suite 101 Styles ── */
  .s101-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
    margin-bottom: 32px;
  }
  .s101-card {
    background: #fff;
    border-radius: var(--radius);
    padding: 26px 24px;
    box-shadow: var(--shadow);
    border-left: 5px solid;
  }
  .s101-card:nth-child(1) { border-color: var(--bubble1); }
  .s101-card:nth-child(2) { border-color: var(--bubble5); }
  .s101-card:nth-child(3) { border-color: var(--bubble2); }
  .s101-card:nth-child(4) { border-color: var(--bubble3); }
  .s101-card:nth-child(5) { border-color: var(--bubble4); }
  .s101-card:nth-child(6) { border-color: var(--bubble6); }
  .s101-card h3 { font-size: 1.05rem; font-weight: 900; color: var(--text); margin-bottom: 10px; }
  .s101-card p  { font-size: .9rem; font-weight: 600; color: var(--text2); line-height: 1.65; }
  .s101-card p strong { color: var(--text); }

  .step-list { list-style: none; margin-top: 10px; }
  .step-list li {
    display: flex; gap: 12px; align-items: flex-start;
    margin-bottom: 10px;
    font-size: .9rem; font-weight: 700; color: var(--text2); line-height: 1.55;
  }
  .step-num {
    flex-shrink: 0;
    width: 28px; height: 28px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--bubble1), var(--bubble5));
    color: #fff;
    font-size: .8rem; font-weight: 900;
    display: inline-flex; align-items: center; justify-content: center;
  }
  .step-num.orange { background: linear-gradient(135deg, var(--bubble2), #e85d04); }

  .faq-item {
    background: #fff;
    border-radius: var(--radius-sm);
    margin-bottom: 12px;
    box-shadow: 0 3px 14px rgba(160,100,200,.09);
    overflow: hidden;
  }
  .faq-q {
    width: 100%;
    text-align: left;
    padding: 16px 20px;
    background: none;
    border: none;
    font-family: 'Nunito', sans-serif;
    font-size: .95rem;
    font-weight: 800;
    color: var(--text);
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 12px;
  }
  .faq-q:hover { background: #fdf4ff; }
  .faq-arrow { transition: transform .25s; font-size: .9rem; }
  .faq-item.open .faq-arrow { transform: rotate(180deg); }
  .faq-a {
    max-height: 0;
    overflow: hidden;
    transition: max-height .35s ease, padding .25s;
    padding: 0 20px;
    font-size: .88rem;
    font-weight: 600;
    color: var(--text2);
    line-height: 1.7;
  }
  .faq-item.open .faq-a { max-height: 400px; padding: 0 20px 18px; }

  .price-table {
    width: 100%;
    border-collapse: collapse;
    background: #fff;
    border-radius: var(--radius);
    overflow: hidden;
    box-shadow: var(--shadow);
    font-size: .88rem;
    font-weight: 700;
  }
  .price-table th {
    background: linear-gradient(135deg, #d4c8ff, #ffd6ec);
    color: var(--text);
    padding: 14px 18px;
    text-align: left;
    font-size: .82rem;
    font-weight: 900;
    letter-spacing: .3px;
  }
  .price-table td { padding: 13px 18px; color: var(--text2); border-top: 1px solid #f3eaff; }
  .price-table tr:hover td { background: #fdf4ff; }
  .price-pill {
    display: inline-block;
    padding: 4px 12px;
    border-radius: 50px;
    font-size: .78rem;
    font-weight: 800;
    background: linear-gradient(135deg, #bbf7d0, #a7f3d0);
    color: #065f46;
  }
  .price-pill.mid { background: linear-gradient(135deg, #fde68a, #fbbf24); color: #92400e; }
  .price-pill.high { background: linear-gradient(135deg, #fecaca, #fca5a5); color: #7f1d1d; }

  .tip-box {
    background: linear-gradient(135deg, #fdf4ff, #eff6ff);
    border-radius: var(--radius);
    padding: 22px 24px;
    margin-bottom: 20px;
    border: 2px dashed #d4c8ff;
    font-size: .9rem;
    font-weight: 700;
    color: var(--text2);
    line-height: 1.65;
  }
  .tip-box strong { color: var(--text); }

  /* ── Footer ── */
  .footer {
    position: relative;
    z-index: 1;
    text-align: center;
    padding: 24px 20px 40px;
    font-size: .85rem;
    font-weight: 700;
    color: var(--text2);
  }
  .footer span { animation: pulse 2s ease-in-out infinite; display: inline-block; }
  @keyframes pulse {
    0%, 100% { transform: scale(1); }
    50%       { transform: scale(1.3); }
  }

  /* ── Responsive ── */
  @media (max-width: 600px) {
    .hero h1 { font-size: 2rem; }
    .venue-grid { grid-template-columns: 1fr; }
    .resell-grid { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>

<!-- Floating background bubbles -->
<div class="bg-bubbles">
  <span></span><span></span><span></span><span></span>
  <span></span><span></span><span></span><span></span>
</div>

<!-- ── HERO ── -->
<div class="hero">
  <span class="hero-emoji">🏟️</span>
  <h1>Arena <span>Suites</span> Directory</h1>
  <p>Your complete guide to premium suite contacts at every major NBA arena & NFL stadium in the USA ✨</p>
</div>

<!-- ── SEARCH ── -->
<div class="search-wrap">
  <span class="search-icon">🔍</span>
  <input type="text" id="searchInput" placeholder="Search arenas, stadiums, cities, teams…">
</div>

<!-- ── TABS ── -->
<div class="tabs">
  <button class="tab-btn active" data-tab="resell">🎟️ Where to Resell</button>
  <button class="tab-btn" data-tab="nba">🏀 NBA Arenas</button>
  <button class="tab-btn" data-tab="nfl">🏈 NFL Stadiums</button>
  <button class="tab-btn" data-tab="s101">📚 Suite 101</button>
</div>

<!-- ── MAIN CONTENT ── -->
<div class="main">

  <!-- COUNT DISPLAY -->
  <div class="count-badge" id="countBadge">
    <span>🎯</span> <span id="countText">Showing all venues</span>
  </div>

  <!-- ─────────────────────── RESELL SECTION ─────────────────────── -->
  <div class="section active" id="section-resell">
    <div class="section-title"><span>🎟️</span> Where to Resell Your Tickets</div>

    <div class="info-banner">
      <p>💡 <strong>Pro Tip:</strong> These are the <strong>most trusted platforms</strong> for reselling luxury suite tickets. List on multiple platforms at once for maximum exposure and the best chance of selling fast!</p>
    </div>

    <div class="resell-grid" id="resellGrid">

      <div class="resell-card" onclick="window.open('https://www.stubhub.com','_blank')">
        <span class="resell-emoji">🎫</span>
        <span class="resell-name">StubHub</span>
        <span class="resell-url">stubhub.com</span>
        <span class="resell-badge">Most Popular</span>
      </div>

      <div class="resell-card" onclick="window.open('https://www.ticketmaster.com','_blank')">
        <span class="resell-emoji">🎭</span>
        <span class="resell-name">Ticketmaster</span>
        <span class="resell-url">ticketmaster.com</span>
        <span class="resell-badge">Trusted Brand</span>
      </div>

      <div class="resell-card" onclick="window.open('https://www.suitehop.com','_blank')">
        <span class="resell-emoji">🏆</span>
        <span class="resell-name">SuiteHop</span>
        <span class="resell-url">suitehop.com</span>
        <span class="resell-badge">Suite Specialist</span>
      </div>

      <div class="resell-card" onclick="window.open('https://www.vividseats.com','_blank')">
        <span class="resell-emoji">💜</span>
        <span class="resell-name">Vivid Seats</span>
        <span class="resell-url">vividseats.com</span>
        <span class="resell-badge">High Volume</span>
      </div>

      <div class="resell-card" onclick="window.open('https://www.seatgeek.com','_blank')">
        <span class="resell-emoji">📍</span>
        <span class="resell-name">SeatGeek</span>
        <span class="resell-url">seatgeeks.com</span>
        <span class="resell-badge">Tech-Forward</span>
      </div>

      <div class="resell-card" onclick="window.open('https://www.suiteexperiencegroup.com','_blank')">
        <span class="resell-emoji">✨</span>
        <span class="resell-name">Suite Experience Group</span>
        <span class="resell-url">suiteexperiencegroup.com</span>
        <span class="resell-badge">Luxury Focus</span>
      </div>

    </div>

    <div class="info-banner" style="margin-top:32px;">
      <p>💰 <strong>How to Sell:</strong> Create a free seller account → List your suite with photos &amp; details → Set your price (check comparable listings first!) → Get paid after the event. Most platforms take <strong>10–15% commission</strong>. Suite Experience Group &amp; SuiteHop specialize in luxury suites so they often attract <strong>higher-value buyers</strong>!</p>
    </div>
  </div>

  <!-- ─────────────────────── NBA SECTION ─────────────────────── -->
  <div class="section" id="section-nba">
    <div class="section-title"><span>🏀</span> NBA Arena Suites</div>

    <div class="info-banner">
      <p>🏀 <strong>NBA Arenas</strong> host all NBA games <em>and most concerts</em>. These are premier mid-size venues perfect for corporate events, birthday parties, or a luxury night out. Click any link to go directly to their premium seating page!</p>
    </div>

    <div class="venue-grid" id="nbaGrid">
    </div>
    <div class="no-results" id="nbaNoResults">😢 No arenas found matching your search. Try a different keyword!</div>
  </div>

  <!-- ─────────────────────── NFL SECTION ─────────────────────── -->
  <div class="section" id="section-nfl">
    <div class="section-title"><span>🏈</span> NFL Stadium Suites</div>

    <div class="info-banner">
      <p>🏈 <strong>NFL Stadiums</strong> host football games <em>AND mega-concerts &amp; events</em>. Think <strong>Beyoncé, Taylor Swift, Michael Jackson tribute tours</strong> — these massive venues attract the biggest acts. Suites here are the ultimate luxury experience!</p>
    </div>

    <div class="venue-grid" id="nflGrid">
    </div>
    <div class="no-results" id="nflNoResults">😢 No stadiums found matching your search. Try a different keyword!</div>
  </div>

  <!-- ─────────────────────── SUITE 101 SECTION ─────────────────────── -->
  <div class="section" id="section-s101">
    <div class="section-title"><span>📚</span> Suite 101 — Everything You Need to Know</div>

    <!-- WHAT IS A SUITE -->
    <div class="info-banner" style="margin-bottom:28px;">
      <p>🙋 <strong>Never been in a suite before? No problem!</strong> This section breaks down everything in plain English — no industry jargon, no confusing stuff. Just real talk about how suites work. ✨</p>
    </div>

    <div class="s101-grid">

      <div class="s101-card">
        <h3>🤔 So... what even IS a suite?</h3>
        <p>Think of a suite like a <strong>private VIP room</strong> inside an arena or stadium. Instead of sitting in regular seats with everyone else, you get your own enclosed (or semi-enclosed) space with comfy seats, a private TV, catering, and sometimes a private bathroom. It's basically like watching the game from a really fancy living room — except you're <strong>inside the actual venue</strong>. Super fancy. Super exclusive.</p>
      </div>

      <div class="s101-card">
        <h3>🏟️ Arenas vs. Stadiums — what's the difference?</h3>
        <p><strong>Arenas</strong> are smaller, indoor venues — they host NBA games and most regular concerts (think: your favorite pop star, comedy shows, etc.). <strong>Stadiums</strong> are the massive outdoor venues for NFL football, and they attract the <strong>MEGA events</strong> — Taylor Swift's Eras Tour, Beyoncé, major world cup events. Stadium suites are generally bigger and pricier because the events are bigger.</p>
      </div>

      <div class="s101-card">
        <h3>👥 Who typically buys suites?</h3>
        <p>Honestly? All kinds of people! Mostly it's <strong>businesses</strong> that buy suites for a full season to entertain clients. But suites are also sold for <strong>single events</strong> — birthdays, anniversaries, corporate nights out, bachelorette parties, or just a super special treat. You don't have to be a billionaire. Splitting a suite among 10–20 people can actually make it super affordable per person!</p>
      </div>

      <div class="s101-card">
        <h3>🎉 What's usually included in a suite?</h3>
        <p>Every venue is different, but most suites include: <strong>private seating for 12–30 people</strong>, a TV inside the suite, climate control (so no freezing in December!), catering options (food &amp; drinks, sometimes included, sometimes add-on), a <strong>private attendant</strong>, premium parking passes, and early venue access. Some suites even have outdoor balcony seats AND an indoor lounge area. Basically, it's the full luxury experience. 🥂</p>
      </div>

      <div class="s101-card">
        <h3>📅 Can I buy a suite for just ONE game or event?</h3>
        <p>Yes! This is called a <strong>"single-game suite"</strong> or <strong>"per-event suite."</strong> Many people think suites are only available as full-season packages — but that's not true! You can rent a suite for a single NBA game, one NFL Sunday, or a specific concert. Single-event suites are the most popular thing to buy AND resell on the platforms in this directory. This is actually how most people get started!</p>
      </div>

      <div class="s101-card">
        <h3>🎟️ What's the difference between a suite and club seats?</h3>
        <p><strong>Club seats</strong> are premium seats in a special section of the arena — think cushier seats, access to a private lounge, better food options, but you're still sitting out in the open with other club members. <strong>Suites</strong> are fully private rooms. Club seats are typically cheaper and easier to get. Suites are the full VIP experience. Both are way better than regular seats, but suites are in a league of their own! 👑</p>
      </div>

    </div>

    <!-- HOW TO BUY -->
    <div class="section-title" style="font-size:1.3rem; margin-top:10px;"><span>🛒</span> How to Buy a Suite (Step by Step)</div>

    <div class="tip-box">
      💡 <strong>Two ways to buy:</strong> You can go directly to the venue (great for season packages), or use a resale marketplace (best for single events and often more flexible pricing). Both are totally legit — it just depends on what you need!
    </div>

    <div class="s101-grid">
      <div class="s101-card">
        <h3>🏟️ Buying Direct from the Venue</h3>
        <ul class="step-list">
          <li><span class="step-num">1</span> Find the venue in the NBA or NFL tab above and click their "Premium Seating Page" link</li>
          <li><span class="step-num">2</span> Browse available suite options (some venues have multiple suite tiers and sizes)</li>
          <li><span class="step-num">3</span> Call or email the premium seating department — the contact info is right here in this directory!</li>
          <li><span class="step-num">4</span> Ask about availability for your date, suite size, catering options, and parking</li>
          <li><span class="step-num">5</span> Review the contract carefully — check what's included, the cancellation policy, and payment terms</li>
          <li><span class="step-num">6</span> Sign, pay, and get ready for the best night ever 🎉</li>
        </ul>
      </div>

      <div class="s101-card">
        <h3>🛍️ Buying from a Resale Platform</h3>
        <ul class="step-list">
          <li><span class="step-num orange">1</span> Head to StubHub, SuiteHop, Vivid Seats, SeatGeek, or Suite Experience Group</li>
          <li><span class="step-num orange">2</span> Search your venue name or event (ex: "Chase Center suite" or "Beyoncé suite")</li>
          <li><span class="step-num orange">3</span> Filter by date and compare listings — prices vary a LOT so shop around!</li>
          <li><span class="step-num orange">4</span> Read the listing carefully — check exactly how many people it fits and what's included</li>
          <li><span class="step-num orange">5</span> Purchase securely through the platform (your money is protected by their buyer guarantee)</li>
          <li><span class="step-num orange">6</span> Get your ticket/access credentials emailed or via the platform's app — show up and enjoy!</li>
        </ul>
      </div>
    </div>

    <!-- HOW TO SELL -->
    <div class="section-title" style="font-size:1.3rem; margin-top:4px;"><span>💸</span> How to Sell a Suite (Step by Step)</div>

    <div class="tip-box">
      💡 <strong>Why would someone sell a suite?</strong> Lots of reasons! Maybe a company bought a season package and can't use certain games. Maybe someone got a suite as a gift and can't attend. Maybe you're a broker who buys and resells for profit. Whatever your reason — here's how to do it the right way!
    </div>

    <div class="s101-grid">
      <div class="s101-card">
        <h3>📸 Step 1 — Know What You're Selling</h3>
        <p>Before you list anything, gather all the details: <strong>venue name, event date, suite number or section, exact capacity</strong> (how many people fit), what's included (food, drinks, parking passes), and any restrictions. The more detail in your listing, the faster it sells. Buyers want to know EXACTLY what they're getting!</p>
      </div>

      <div class="s101-card">
        <h3>💰 Step 2 — Price It Right</h3>
        <p>Search the same event on the resale platforms BEFORE setting your price. See what similar suites are listed for and <strong>price competitively</strong>. Don't go too low (you're leaving money on the table) and don't go too high (you'll sit unsold). A good starting point: match the lowest competitor, then adjust based on demand. Big events = you can charge more. Regular season games = be more competitive.</p>
      </div>

      <div class="s101-card">
        <h3>📢 Step 3 — List on Multiple Platforms</h3>
        <p>Don't just list on one site! Put your suite on <strong>StubHub + SuiteHop + Vivid Seats</strong> at minimum. More platforms = more eyeballs = faster sale. Just make sure to remove the listing everywhere else the moment it sells so you don't accidentally double-sell. Pro tip: SuiteHop and Suite Experience Group are specialist platforms that attract buyers who specifically want suites — they're often worth the extra effort to list there!</p>
      </div>

      <div class="s101-card">
        <h3>⏰ Step 4 — Timing Matters!</h3>
        <p>The best time to sell is <strong>2–6 weeks before the event</strong> for regular games, and <strong>1–3 months out</strong> for big concerts or playoff games. If you wait too close to the event, buyers get nervous it's a scam. Too early and there's not enough urgency. Sweet spot is a few weeks out when people are actively planning. If it's not sold a week out, consider dropping the price — an unsold suite makes zero dollars!</p>
      </div>

      <div class="s101-card">
        <h3>🤝 Step 5 — Transfer the Tickets Properly</h3>
        <p>Once it sells, you'll transfer the tickets digitally through the platform. <strong>Never just email someone your ticket PDF</strong> without going through the platform — this isn't protected and can lead to disputes. Most platforms handle the transfer for you. The buyer gets their credentials, you get paid (usually 24–72 hours after the event ends). Easy!</p>
      </div>

      <div class="s101-card">
        <h3>🧾 Step 6 — Understand Platform Fees</h3>
        <p>Every platform takes a cut. Here's the rough breakdown: <strong>StubHub</strong> takes ~15% seller fee. <strong>Vivid Seats</strong> takes ~10%. <strong>SeatGeek</strong> ~10–12%. <strong>SuiteHop</strong> and <strong>Suite Experience Group</strong> fees vary — but they often bring in higher-value buyers so you can price higher. Always factor in fees when setting your list price so you still hit your target profit!</p>
      </div>
    </div>

    <!-- PRICING TABLE -->
    <div class="section-title" style="font-size:1.3rem; margin-top:4px;"><span>💲</span> Suite Pricing — Rough Ballpark Guide</div>

    <div class="tip-box">
      ⚠️ <strong>Heads up:</strong> Prices vary WILDLY based on the event, venue, city, and demand. These are rough ballparks to give you an idea — always check the actual platform for real-time pricing!
    </div>

    <div style="overflow-x:auto; margin-bottom:32px;">
      <table class="price-table">
        <thead>
          <tr>
            <th>Event Type</th>
            <th>Venue Type</th>
            <th>Typical Suite Price</th>
            <th>People It Fits</th>
            <th>Price Per Person</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Regular Season NBA Game</td>
            <td>Arena</td>
            <td>$2,000 – $6,000</td>
            <td>12–20 people</td>
            <td><span class="price-pill">$100–$400/person</span></td>
          </tr>
          <tr>
            <td>NBA Playoff Game</td>
            <td>Arena</td>
            <td>$8,000 – $25,000+</td>
            <td>12–20 people</td>
            <td><span class="price-pill mid">$400–$1,500/person</span></td>
          </tr>
          <tr>
            <td>Regular Season NFL Game</td>
            <td>Stadium</td>
            <td>$5,000 – $15,000</td>
            <td>16–30 people</td>
            <td><span class="price-pill">$200–$600/person</span></td>
          </tr>
          <tr>
            <td>NFL Playoff / Super Bowl</td>
            <td>Stadium</td>
            <td>$30,000 – $200,000+</td>
            <td>16–30 people</td>
            <td><span class="price-pill high">$1,000–$8,000+/person</span></td>
          </tr>
          <tr>
            <td>Mid-Size Concert (arena)</td>
            <td>Arena</td>
            <td>$3,000 – $10,000</td>
            <td>12–20 people</td>
            <td><span class="price-pill">$150–$600/person</span></td>
          </tr>
          <tr>
            <td>MEGA Concert (stadium)</td>
            <td>Stadium</td>
            <td>$15,000 – $80,000+</td>
            <td>16–30 people</td>
            <td><span class="price-pill mid">$500–$3,500/person</span></td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- FAQ -->
    <div class="section-title" style="font-size:1.3rem; margin-top:4px;"><span>❓</span> FAQ — Questions People Always Ask</div>

    <div id="faqContainer">

      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">
          Can I bring my own food and drinks into a suite? <span class="faq-arrow">▼</span>
        </button>
        <div class="faq-a">Usually NO for alcohol — venues have strict policies about outside drinks. But some venues allow outside food (especially for dietary restrictions). Most suites come with catering options you can pre-order, and there's usually in-suite bar service you can purchase. When you book, just ask the catering team about your options. Some venues are super flexible, others are strict. Always ask upfront!</div>
      </div>

      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">
          Is parking included when I buy a suite? <span class="faq-arrow">▼</span>
        </button>
        <div class="faq-a">Sometimes yes, sometimes no — it depends on the venue and the specific suite package. Most full-season suite packages include parking passes. Single-event suites bought directly from the venue often include 2–4 parking passes. Suites bought on resale platforms may or may not include parking — read the listing carefully! Always confirm before you buy, because game-day parking near major venues can cost $40–$100+.</div>
      </div>

      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">
          What if I can't fill the whole suite? Is that okay? <span class="faq-arrow">▼</span>
        </button>
        <div class="faq-a">Totally fine! Suites have a max capacity, not a minimum. If your suite fits 20 people and only 8 show up, that's your business. Some people even buy a suite for a smaller group just because they want the privacy and luxury. And if you CAN'T fill it, you can sell individual "suite tickets" on platforms like StubHub — listing individual seats in your suite and selling them separately to recover some of your cost.</div>
      </div>

      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">
          Is it safe to buy a suite on a resale site? How do I know it's not a scam? <span class="faq-arrow">▼</span>
        </button>
        <div class="faq-a">Stick to the major platforms listed in this directory and you're protected! StubHub, Vivid Seats, SeatGeek, and SuiteHop all have buyer guarantees — if your tickets aren't valid, they'll refund you or find replacements. The key rule: NEVER buy from someone on Craigslist, Facebook Marketplace, or random DMs. Only buy through platforms that offer buyer protection. If the deal seems too good to be true... it probably is 🚩</div>
      </div>

      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">
          How far in advance should I reach out to a venue about suites? <span class="faq-arrow">▼</span>
        </button>
        <div class="faq-a">For season packages, venues start selling anywhere from 3–6 months before the season begins, so reach out early! For specific events (concerts, playoffs), you typically need to contact them at least 1–3 months in advance for the best selection. The most popular venues — like Madison Square Garden, Chase Center, AT&T Stadium — sell out FAST. Don't wait! For resale platforms, you'll find inventory up until literally hours before the event.</div>
      </div>

      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">
          What's the best venue for a concert suite experience? <span class="faq-arrow">▼</span>
        </button>
        <div class="faq-a">For pure concert experience, NBA arenas like Chase Center (SF), Madison Square Garden (NYC), Crypto.com Arena (LA), and TD Garden (Boston) are legendary. For MEGA concerts, NFL stadiums like SoFi Stadium, AT&T Stadium, and Allegiant Stadium have world-class production setups. But honestly? Any suite is a great concert experience — you have privacy, great sightlines, your own space, and no one spilling beer on you 😂</div>
      </div>

      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">
          Do I need to tip the suite attendant? <span class="faq-arrow">▼</span>
        </button>
        <div class="faq-a">This is a great question! Yes — it's standard practice to tip your suite attendant. They handle everything from food orders to extra requests all night. A good rule of thumb: tip $20–$50 per attendant depending on the service and how big your group is. If you order a lot of food and drinks and they're really hustling, go higher. It's also just good karma — these folks work hard to make your night special! 🙏</div>
      </div>

      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">
          Can suites be used for events other than games and concerts? <span class="faq-arrow">▼</span>
        </button>
        <div class="faq-a">Yes! Many arenas and stadiums rent suites for non-event days too — think corporate meetings, holiday parties, product launches, filming, or private dinners. These are called "dark suite" or "non-event suite" rentals. Pricing is usually lower since there's no game happening, but the space and amenities are still incredible. Contact the venue's premium events or corporate sales team (different from the premium seating team) to ask about this.</div>
      </div>

    </div>

  </div>

</div>

<!-- ── FOOTER ── -->
<div class="footer">
  Made with <span>💜</span> &nbsp;|&nbsp; Arena Suites Directory &nbsp;|&nbsp; Always verify contact info before reaching out!
</div>

<script>
// ── DATA ──────────────────────────────────────────────────────────────────
const nbaData = [
  { num:1,  name:"American Airlines Center",     team:"Dallas Mavericks",          city:"Dallas, TX",              phone:"+1 (214) 665-4222", email:"PremiumSeating@americanairlinescenter.com", website:"https://www.americanairlinescenter.com/premium/premium-seating" },
  { num:2,  name:"Amway Center",                 team:"Orlando Magic",              city:"Orlando, FL",             phone:"+1 (407) 896-2442", email:"premiumseating@orlandomagic.com",           website:"https://www.amwaycenter.com/premium-seating" },
  { num:3,  name:"Ball Arena",                   team:"Denver Nuggets",             city:"Denver, CO",              phone:"+1 (303) 405-6161", email:"premiumservices@teamkse.com",               website:"https://www.ballarena.com/premium" },
  { num:4,  name:"Barclays Center",              team:"Brooklyn Nets",              city:"Brooklyn, NY",            phone:"+1 (718) 942-9661", email:"premium@barclayscenter.com",               website:"https://www.barclayscenter.com/premium" },
  { num:5,  name:"Capital One Arena",            team:"Washington Wizards",         city:"Washington, D.C.",        phone:"+1 (202) 661-5061", email:"suites@monumentalsports.com",              website:"https://www.capitalonearena.com/premium-seating" },
  { num:6,  name:"Chase Center",                 team:"Golden State Warriors",      city:"San Francisco, CA",       phone:"+1 (877) 479-4667", email:"premium@warriors.com",                     website:"https://www.chasecenter.com/premium" },
  { num:7,  name:"Crypto.com Arena",             team:"Los Angeles Lakers",         city:"Los Angeles, CA",         phone:"+1 (877) 234-8425", email:"premiumevents@lakers.com",                 website:"https://www.cryptocomarena.com/premium-seating" },
  { num:8,  name:"Delta Center",                 team:"Utah Jazz",                  city:"Salt Lake City, UT",      phone:"+1 (801) 325-2203", email:"premiumseating@utahjazz.com",              website:"https://www.utahjazz.com/premium-seating" },
  { num:9,  name:"FedExForum",                   team:"Memphis Grizzlies",          city:"Memphis, TN",             phone:"+1 (901) 205-1445", email:"premiumsales@grizzlies.com",               website:"https://www.nba.com/grizzlies/tickets/premium-seating" },
  { num:10, name:"Fiserv Forum",                 team:"Milwaukee Bucks",            city:"Milwaukee, WI",           phone:"+1 (414) 227-0847", email:"premiumsuites@bucks.com",                  website:"https://www.fiservforum.com/premium" },
  { num:11, name:"Footprint Center",             team:"Phoenix Suns",               city:"Phoenix, AZ",             phone:"+1 (602) 379-7525", email:"premium@phxses.com",                       website:"https://www.footprintcenter.com/premium-seating" },
  { num:12, name:"Frost Bank Center",            team:"San Antonio Spurs",          city:"San Antonio, TX",         phone:"+1 (210) 444-5657", email:"premiumservices@spurs.com",                website:"https://www.nba.com/spurs/tickets/premium-seating" },
  { num:13, name:"Gainbridge Fieldhouse",        team:"Indiana Pacers",             city:"Indianapolis, IN",        phone:"+1 (317) 917-2859", email:"premiumseating@pacers.com",                website:"https://www.gainbridgefieldhouse.com/premium-seating/" },
  { num:14, name:"Golden 1 Center",              team:"Sacramento Kings",           city:"Sacramento, CA",          phone:"+1 (916) 840-5745", email:"premiumseating@kings.com",                 website:"https://www.kings.com/golden1center" },
  { num:15, name:"Kaseya Center",                team:"Miami Heat",                 city:"Miami, FL",               phone:"+1 (786) 777-1460", email:"premiumsales@heat.com",                    website:"https://www.kaseyacenter.com/premium-seating" },
  { num:16, name:"Little Caesars Arena",         team:"Detroit Pistons",            city:"Detroit, MI",             phone:"+1 (313) 471-3333", email:"premiumseating@olyent.com",                website:"https://www.313presents.com/premium-seating/little-caesars-arena" },
  { num:17, name:"Moda Center",                  team:"Portland Trail Blazers",     city:"Portland, OR",            phone:"+1 (503) 963-3972", email:"premiumseating@trailblazers.com",           website:"https://www.nba.com/blazers/premium-seating" },
  { num:18, name:"Paycom Center",                team:"OKC Thunder",                city:"Oklahoma City, OK",       phone:"+1 (405) 208-4666", email:"premiumseating@okcthunder.com",            website:"https://www.paycomcenter.com/premium-seating" },
  { num:19, name:"Rocket Mortgage FieldHouse",   team:"Cleveland Cavaliers",        city:"Cleveland, OH",           phone:"+1 (216) 420-2481", email:"premierseating@cavs.com",                  website:"https://www.rocketmortgagefieldhouse.com/premium-seating" },
  { num:20, name:"Smoothie King Center",         team:"New Orleans Pelicans",       city:"New Orleans, LA",         phone:"+1 (504) 525-4667", email:"premiumseating@pelicans.com",              website:"https://www.smoothiekingcenter.com/premium-seating" },
  { num:21, name:"Spectrum Center",              team:"Charlotte Hornets",          city:"Charlotte, NC",           phone:"+1 (704) 688-8901", email:"premiumsuites@hornets.com",                website:"https://www.spectrumcentercharlotte.com/premium-seating" },
  { num:22, name:"State Farm Arena",             team:"Atlanta Hawks",              city:"Atlanta, GA",             phone:"+1 (866) 715-1500", email:"premiumsales@hawks.com",                   website:"https://www.statefarmarena.com/premium-seating" },
  { num:23, name:"Target Center",                team:"Minnesota Timberwolves",     city:"Minneapolis, MN",         phone:"+1 (612) 673-1234", email:"premiumseating@timberwolves.com",           website:"https://www.nba.com/timberwolves/tickets/premium-seating" },
  { num:24, name:"TD Garden",                    team:"Boston Celtics",             city:"Boston, MA",              phone:"+1 (617) 624-1847", email:"premiumsales@tdgarden.com",                website:"https://www.tdgarden.com/premium/seating-options" },
  { num:25, name:"Toyota Center",                team:"Houston Rockets",            city:"Houston, TX",             phone:"+1 (713) 758-7295", email:"premiumseats@rocketball.com",              website:"https://www.toyotacenter.com/premium-seating" },
  { num:26, name:"United Center",                team:"Chicago Bulls",              city:"Chicago, IL",             phone:"+1 (312) 455-4000", email:"suites@unitedcenter.com",                  website:"https://www.unitedcenter.com/premium-seating/suites/" },
  { num:27, name:"Wells Fargo Center",           team:"Philadelphia 76ers",         city:"Philadelphia, PA",        phone:"+1 (215) 339-7676", email:"premiumservices@wfcphilly.com",            website:"https://www.wellsfargocenterphilly.com/premium-seating" },
  { num:28, name:"Madison Square Garden",        team:"New York Knicks",            city:"New York, NY",            phone:"+1 (212) 465-6771", email:"suites@msg.com",                           website:"https://www.msg.com/madison-square-garden/premium-experiences" },
];

const nflData = [
  { num:1,  name:"Acrisure Stadium",             team:"Pittsburgh Steelers",        city:"Pittsburgh, PA",          phone:"+1 (412) 697-7597", email:"suites@steelers.com",                     website:"https://www.steelers.com/tickets/premium/" },
  { num:2,  name:"Allegiant Stadium",            team:"Las Vegas Raiders",          city:"Paradise, NV",            phone:"+1 (800) 724-3377", email:"suites@raiders.com",                      website:"https://www.raiders.com/tickets/premium/" },
  { num:3,  name:"AT&T Stadium",                 team:"Dallas Cowboys",             city:"Arlington, TX",           phone:"+1 (817) 892-4470", email:"suites@dallascowboys.net",                website:"https://www.dallascowboys.com/premium/" },
  { num:4,  name:"Bank of America Stadium",      team:"Carolina Panthers",          city:"Charlotte, NC",           phone:"+1 (704) 358-7800", email:"premiumseating@panthers.com",             website:"https://www.panthers.com/tickets/premium/" },
  { num:5,  name:"Caesars Superdome",            team:"New Orleans Saints",         city:"New Orleans, LA",         phone:"+1 (504) 587-3663", email:"suites@saints.nfl.com",                   website:"https://www.neworleanssaints.com/tickets/premium/" },
  { num:6,  name:"Cleveland Browns Stadium",     team:"Cleveland Browns",           city:"Cleveland, OH",           phone:"+1 (440) 891-5050", email:"premiumseating@clevelandbrowns.com",      website:"https://www.clevelandbrowns.com/tickets/premium-seating/" },
  { num:7,  name:"Empower Field at Mile High",   team:"Denver Broncos",             city:"Denver, CO",              phone:"+1 (720) 258-3338", email:"premiumseating@broncos.nfl.net",          website:"https://www.denverbroncos.com/tickets/premium/" },
  { num:8,  name:"EverBank Stadium",             team:"Jacksonville Jaguars",       city:"Jacksonville, FL",        phone:"+1 (904) 633-2000", email:"premiumseating@jaguars.com",              website:"https://www.jaguars.com/tickets/premium/" },
  { num:9,  name:"FedExField",                   team:"Washington Commanders",      city:"Landover, MD",            phone:"+1 (301) 276-6800", email:"suites@commanders.com",                   website:"https://www.commanders.com/tickets/premium/" },
  { num:10, name:"Ford Field",                   team:"Detroit Lions",              city:"Detroit, MI",             phone:"+1 (313) 262-2222", email:"premiumseating@detroitlions.com",          website:"https://www.fordfield.com/tickets/premium-seating/" },
  { num:11, name:"GEHA Field at Arrowhead",      team:"Kansas City Chiefs",         city:"Kansas City, MO",         phone:"+1 (816) 920-4839", email:"suites@chiefs.nfl.com",                   website:"https://www.chiefs.com/tickets/premium/" },
  { num:12, name:"Gillette Stadium",             team:"New England Patriots",       city:"Foxborough, MA",          phone:"+1 (508) 384-4378", email:"suites@gillettestadium.com",              website:"https://www.patriots.com/tickets/premium/" },
  { num:13, name:"Hard Rock Stadium",            team:"Miami Dolphins",             city:"Miami Gardens, FL",       phone:"+1 (305) 943-7980", email:"premium@dolphins.com",                    website:"https://www.miamidolphins.com/tickets/premium/" },
  { num:14, name:"Highmark Stadium",             team:"Buffalo Bills",              city:"Orchard Park, NY",        phone:"+1 (716) 312-8900", email:"premiumseating@bills.nfl.net",            website:"https://www.buffalobills.com/tickets/premium-seating" },
  { num:15, name:"Levi's Stadium",               team:"San Francisco 49ers",        city:"Santa Clara, CA",         phone:"+1 (415) 464-9377", email:"premiumservices@49ers.com",               website:"https://www.levisstadium.com/premium-seating/" },
  { num:16, name:"Lincoln Financial Field",      team:"Philadelphia Eagles",        city:"Philadelphia, PA",        phone:"+1 (215) 463-5500", email:"premium@eagles.nfl.net",                  website:"https://www.lincolnfinancialfield.com/premium-seating/" },
  { num:17, name:"Lambeau Field",                team:"Green Bay Packers",          city:"Green Bay, WI",           phone:"+1 (920) 569-7260", email:"suites@packers.com",                      website:"https://www.packers.com/tickets/premium/" },
  { num:18, name:"Lumen Field",                  team:"Seattle Seahawks",           city:"Seattle, WA",             phone:"+1 (888) 246-4000", email:"premiumsales@seahawks.com",               website:"https://www.seahawks.com/tickets/premium/" },
  { num:19, name:"Lucas Oil Stadium",            team:"Indianapolis Colts",         city:"Indianapolis, IN",        phone:"+1 (317) 808-5388", email:"premiumseating@colts.nfl.net",            website:"https://www.colts.com/tickets/premium/" },
  { num:20, name:"M&T Bank Stadium",             team:"Baltimore Ravens",           city:"Baltimore, MD",           phone:"+1 (410) 261-7283", email:"clubseatsuitesales@ravens.nfl.net",       website:"https://www.baltimoreravens.com/tickets/premium-seating/" },
  { num:21, name:"Mercedes-Benz Stadium",        team:"Atlanta Falcons",            city:"Atlanta, GA",             phone:"+1 (470) 341-4555", email:"premiumsales@mercedesbenzstadium.com",    website:"https://mercedesbenzstadium.com/premium-seating/" },
  { num:22, name:"MetLife Stadium",              team:"NY Giants / NY Jets",        city:"East Rutherford, NJ",     phone:"+1 (201) 559-1515", email:"suites@metlifestadium.com",               website:"https://www.metlifestadium.com/guest-services/private-suites/" },
  { num:23, name:"NRG Stadium",                  team:"Houston Texans",             city:"Houston, TX",             phone:"+1 (832) 667-2390", email:"premiumseating@houstontexans.com",         website:"https://www.houstontexans.com/season-ticket-members/club-season-ticket-membership" },
  { num:24, name:"Nissan Stadium",               team:"Tennessee Titans",           city:"Nashville, TN",           phone:"+1 (615) 565-4200", email:"premiumseating@titans.nfl.net",           website:"https://www.tennesseetitans.com/tickets/premium/" },
  { num:25, name:"Paycor Stadium",               team:"Cincinnati Bengals",         city:"Cincinnati, OH",          phone:"+1 (513) 621-8383", email:"suites@bengals.nfl.net",                  website:"https://www.bengals.com/tickets/suites-and-clubs" },
  { num:26, name:"Raymond James Stadium",        team:"Tampa Bay Buccaneers",       city:"Tampa, FL",               phone:"+1 (813) 998-3877", email:"premium@buccaneers.nfl.net",              website:"https://www.buccaneers.com/tickets/premium/" },
  { num:27, name:"SoFi Stadium",                 team:"LA Chargers / LA Rams",      city:"Inglewood, CA",           phone:"+1 (818) 540-4340", email:"premiumseating@sofi.com",                 website:"https://www.sofistadium.com/premium-seating/" },
  { num:28, name:"Soldier Field",                team:"Chicago Bears",              city:"Chicago, IL",             phone:"+1 (888) 792-3277", email:"suite_sales@bears.nfl.net",               website:"https://www.chicagobears.com/tickets/premium/" },
  { num:29, name:"State Farm Stadium",           team:"Arizona Cardinals",          city:"Glendale, AZ",            phone:"+1 (602) 379-0102", email:"premiumsuites@cardinals.nfl.net",         website:"https://www.azcardinals.com/tickets/premium-seating/" },
  { num:30, name:"U.S. Bank Stadium",            team:"Minnesota Vikings",          city:"Minneapolis, MN",         phone:"+1 (952) 918-8599", email:"premium@vikings.nfl.net",                 website:"https://www.vikings.com/tickets/premium/" },
  { num:31, name:"TIAA Bank Field",              team:"Jacksonville Jaguars",       city:"Jacksonville, FL",        phone:"+1 (904) 633-2000", email:"premiumseating@jaguars.com",              website:"https://www.jaguars.com/tickets/premium/" },
];

// ── RENDER ────────────────────────────────────────────────────────────────
function buildCard(v, cssClass) {
  const id = cssClass + v.num;
  return `
    <div class="venue-card ${cssClass}" data-search="${(v.name + ' ' + v.team + ' ' + v.city).toLowerCase()}" id="${id}">
      <span class="venue-number">${v.num}</span>
      <div class="venue-name">${v.name}</div>
      <div class="venue-team">🏙️ ${v.team} &nbsp;·&nbsp; ${v.city}</div>
      <hr class="venue-divider">
      <div class="venue-info-row">
        <span class="ico">📞</span>
        <span><a href="tel:${v.phone.replace(/\s/g,'')}">${v.phone}</a></span>
      </div>
      <div class="venue-info-row">
        <span class="ico">✉️</span>
        <span><a href="mailto:${v.email}">${v.email}</a></span>
      </div>
      <div class="venue-info-row">
        <span class="ico">🌐</span>
        <span><a href="${v.website}" target="_blank" rel="noopener">Premium Seating Page ↗</a></span>
      </div>
      <button class="copy-btn" onclick="copyContact(event, '${v.name}', '${v.phone}', '${v.email}', '${v.website}')">
        📋 Copy Contact Info
      </button>
    </div>
  `;
}

document.getElementById('nbaGrid').innerHTML = nbaData.map(v => buildCard(v, 'nba-card')).join('');
document.getElementById('nflGrid').innerHTML = nflData.map(v => buildCard(v, 'nfl-card')).join('');

// ── TABS ─────────────────────────────────────────────────────────────────
let currentTab = 'resell';
document.querySelectorAll('.tab-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
    btn.classList.add('active');
    currentTab = btn.dataset.tab;
    document.getElementById('section-' + currentTab).classList.add('active');
    updateCount();
    applySearch(document.getElementById('searchInput').value.toLowerCase());
  });
});

// ── SEARCH ────────────────────────────────────────────────────────────────
document.getElementById('searchInput').addEventListener('input', e => {
  applySearch(e.target.value.toLowerCase());
});

function applySearch(q) {
  if (currentTab === 's101') {
    document.getElementById('countBadge').style.display = 'none';
    return;
  }
  document.getElementById('countBadge').style.display = 'flex';
  if (currentTab === 'resell') {
    // filter resell cards by name
    let shown = 0;
    document.querySelectorAll('.resell-card').forEach(card => {
      const text = card.querySelector('.resell-name').textContent.toLowerCase();
      const match = !q || text.includes(q);
      card.style.display = match ? '' : 'none';
      if (match) shown++;
    });
    updateCountText(shown, 'platforms');
    return;
  }

  const grid = currentTab === 'nba' ? 'nbaGrid' : 'nflGrid';
  const noRes = currentTab === 'nba' ? 'nbaNoResults' : 'nflNoResults';
  const cards = document.querySelectorAll(`#${grid} .venue-card`);
  let shown = 0;
  cards.forEach(card => {
    const match = !q || card.dataset.search.includes(q);
    card.style.display = match ? '' : 'none';
    if (match) shown++;
  });
  document.getElementById(noRes).classList.toggle('show', shown === 0);
  updateCountText(shown, currentTab === 'nba' ? 'arenas' : 'stadiums');
}

function updateCount() {
  const q = document.getElementById('searchInput').value.toLowerCase();
  applySearch(q);
}

// ── FAQ TOGGLE ────────────────────────────────────────────────────────────
function toggleFaq(btn) {
  const item = btn.closest('.faq-item');
  const isOpen = item.classList.contains('open');
  document.querySelectorAll('.faq-item').forEach(i => i.classList.remove('open'));
  if (!isOpen) item.classList.add('open');
}

function updateCountText(n, label) {
  const badge = document.getElementById('countBadge');
  const text = document.getElementById('countText');
  if (!document.getElementById('searchInput').value) {
    text.textContent = `Showing all ${n} ${label}`;
    badge.style.display = 'flex';
  } else {
    text.textContent = `${n} ${label} found`;
    badge.style.display = 'flex';
  }
}

// initial count
updateCountText(6, 'platforms');

// ── COPY CONTACT ─────────────────────────────────────────────────────────
function copyContact(e, name, phone, email, website) {
  e.stopPropagation();
  const btn = e.currentTarget;
  const text = `${name}\nPhone: ${phone}\nEmail: ${email}\nWebsite: ${website}`;
  navigator.clipboard.writeText(text).then(() => {
    btn.textContent = '✅ Copied!';
    btn.classList.add('copied');
    setTimeout(() => {
      btn.innerHTML = '📋 Copy Contact Info';
      btn.classList.remove('copied');
    }, 2000);
  }).catch(() => {
    btn.textContent = '⚠️ Try again';
    setTimeout(() => { btn.innerHTML = '📋 Copy Contact Info'; }, 1500);
  });
}
</script>
</body>
</html>
