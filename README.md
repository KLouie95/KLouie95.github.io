<!doctype html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Okinawa → Tokyo — 16 Nights</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Shippori+Mincho:wght@500;700;800&family=Work+Sans:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#1C1B18;
    --indigo-900:#16233B;
    --indigo-700:#23405F;
    --indigo-500:#33587F;
    --paper:#F3ECD9;
    --paper-card:#FBF7EC;
    --paper-dim:#E9E0C9;
    --kaki:#B5622E;
    --kaki-soft:#E7C6AE;
    --moss:#5C6E4A;
    --moss-soft:#DCE2CE;
    --line:#C9C0AC;
    --shadow: 0 1px 0 rgba(28,27,24,0.06), 0 8px 24px -12px rgba(22,35,59,0.25);
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:var(--paper);
    color:var(--ink);
    font-family:'Work Sans', sans-serif;
    -webkit-font-smoothing:antialiased;
  }
  ::selection{ background:var(--kaki-soft); }

  h1,h2,h3,.display{
    font-family:'Shippori Mincho', serif;
    letter-spacing:-0.01em;
    margin:0;
  }
  .mono{ font-family:'JetBrains Mono', monospace; }

  a{ color:inherit; }

  /* progress rail */
  #progress-rail{
    position:fixed;
    left:0; top:0;
    width:4px; height:100vh;
    background:rgba(22,35,59,0.08);
    z-index:50;
  }
  #progress-fill{
    width:100%; height:0%;
    background:linear-gradient(180deg, var(--kaki), var(--indigo-700));
    transition:height 60ms linear;
  }

  /* sticky mini bar */
  #minibar{
    position:sticky; top:0; z-index:40;
    display:flex; align-items:center; justify-content:space-between;
    gap:1rem;
    padding:0.65rem 1.25rem;
    background:rgba(243,236,217,0.92);
    backdrop-filter:blur(6px);
    border-bottom:1px solid var(--line);
    font-size:0.72rem;
    text-transform:uppercase;
    letter-spacing:0.08em;
  }
  #minibar .title{ font-weight:700; color:var(--indigo-900); }
  #minibar .stats{ display:flex; gap:1.1rem; color:var(--indigo-700); }
  #minibar .stats span b{ color:var(--kaki); font-weight:700; }

  /* hero */
  .hero{
    position:relative;
    background:
      radial-gradient(circle at 85% 15%, rgba(181,98,46,0.35), transparent 45%),
      radial-gradient(circle at 10% 90%, rgba(92,110,74,0.35), transparent 40%),
      var(--indigo-900);
    color:var(--paper);
    padding:5rem 1.5rem 3.5rem;
    overflow:hidden;
  }
  .hero-inner{ max-width:760px; margin:0 auto; position:relative; z-index:2; }
  .hero .eyebrow{
    font-family:'JetBrains Mono', monospace;
    font-size:0.72rem;
    letter-spacing:0.14em;
    text-transform:uppercase;
    color:var(--kaki-soft);
    margin-bottom:1rem;
    display:flex; align-items:center; gap:0.6rem;
  }
  .hero .eyebrow::before{
    content:''; width:26px; height:1px; background:var(--kaki-soft);
  }
  .hero h1{
    font-size:clamp(2.1rem, 5vw, 3.4rem);
    line-height:1.05;
    font-weight:700;
    color:#fff;
  }
  .hero h1 em{ font-style:normal; color:var(--kaki-soft); }
  .hero p.sub{
    margin-top:1.1rem;
    font-size:1.05rem;
    max-width:46ch;
    color:rgba(243,236,217,0.78);
    line-height:1.55;
  }
  .hero .for{
    margin-top:1.6rem;
    font-family:'JetBrains Mono', monospace;
    font-size:0.78rem;
    color:rgba(243,236,217,0.55);
  }

  /* stat strip */
  .stat-strip{
    display:grid;
    grid-template-columns:repeat(4,1fr);
    max-width:760px;
    margin:0 auto;
    transform:translateY(2.4rem);
    position:relative; z-index:3;
    background:var(--paper-card);
    border:1px solid var(--line);
    box-shadow:var(--shadow);
  }
  .stat-strip .stat{
    padding:1.1rem 1rem;
    text-align:center;
    border-right:1px solid var(--line);
  }
  .stat-strip .stat:last-child{ border-right:none; }
  .stat-strip .num{
    font-family:'JetBrains Mono', monospace;
    font-weight:700;
    font-size:1.35rem;
    color:var(--indigo-900);
  }
  .stat-strip .label{
    font-size:0.66rem;
    text-transform:uppercase;
    letter-spacing:0.08em;
    color:var(--indigo-700);
    margin-top:0.25rem;
  }

  main.route{
    max-width:760px;
    margin:4.5rem auto 0;
    padding:0 1.5rem 2rem;
    position:relative;
  }

  /* spine */
  .spine-line{
    position:absolute;
    left:1.9rem;
    top:0.4rem; bottom:0.4rem;
    width:2px;
    background:repeating-linear-gradient(180deg, var(--line) 0 6px, transparent 6px 11px);
  }
  @media (max-width:640px){
    .spine-line{ left:1.15rem; }
  }

  /* stop card */
  .stop{
    position:relative;
    padding-left:4.4rem;
    margin-bottom:0.4rem;
    opacity:0;
    transform:translateY(14px);
    transition:opacity 0.6s ease, transform 0.6s ease;
  }
  .stop.in{ opacity:1; transform:translateY(0); }
  @media (max-width:640px){ .stop{ padding-left:2.9rem; } }

  .stop .dot{
    position:absolute;
    left:1.9rem; top:0.55rem;
    width:14px; height:14px;
    border-radius:50%;
    background:var(--paper);
    border:2px solid var(--indigo-700);
    transform:translateX(-50%);
    z-index:2;
  }
  .stop.cycling .dot{ border-color:var(--moss); }
  @media (max-width:640px){ .stop .dot{ left:1.15rem; } }

  .stop-card{
    background:var(--paper-card);
    border:1px solid var(--line);
    box-shadow:var(--shadow);
    padding:1.35rem 1.4rem 1.5rem;
  }
  .stop-head{
    display:flex; align-items:baseline; justify-content:space-between; gap:1rem;
    flex-wrap:wrap;
    border-bottom:1px solid var(--paper-dim);
    padding-bottom:0.7rem;
    margin-bottom:0.85rem;
  }
  .stop-head .place{
    font-family:'JetBrains Mono', monospace;
    font-size:0.7rem;
    letter-spacing:0.1em;
    text-transform:uppercase;
    color:var(--kaki);
    font-weight:700;
  }
  .stop-head .dates{
    font-family:'JetBrains Mono', monospace;
    font-size:0.72rem;
    color:var(--indigo-700);
  }
  .hotel-name{
    font-size:1.28rem;
    font-weight:700;
    color:var(--indigo-900);
    margin-bottom:0.35rem;
  }
  .note{
    font-size:0.92rem;
    line-height:1.55;
    color:#3a382f;
    max-width:56ch;
  }
  .meta-row{
    display:flex; align-items:center; gap:0.7rem; flex-wrap:wrap;
    margin-top:0.9rem;
  }
  .chip{
    font-family:'JetBrains Mono', monospace;
    font-size:0.68rem;
    letter-spacing:0.05em;
    padding:0.28rem 0.55rem;
    border:1px solid var(--line);
    background:var(--paper);
    color:var(--indigo-700);
  }
  .chip.rate{ color:var(--indigo-900); font-weight:700; }
  .chip.accor{
    background:var(--indigo-900); color:var(--paper); border-color:var(--indigo-900);
  }
  .chip.cyc{
    background:var(--moss-soft); color:var(--moss); border-color:var(--moss);
  }

  /* side trip */
  .side-trip{
    margin-top:1rem;
    padding:0.85rem 1rem;
    border:1px dashed var(--line);
    background:var(--paper);
    display:flex; gap:0.8rem; align-items:flex-start;
  }
  .side-trip .icon{ font-size:1.1rem; line-height:1.4; }
  .side-trip .txt b{ display:block; font-size:0.86rem; color:var(--indigo-900); margin-bottom:0.15rem;}
  .side-trip .txt span{ font-size:0.82rem; color:#4a4838; line-height:1.5; }

  /* connector */
  .connector{
    position:relative;
    padding:1.1rem 0 1.1rem 4.4rem;
    opacity:0;
    transform:translateY(10px);
    transition:opacity 0.6s ease, transform 0.6s ease;
  }
  .connector.in{ opacity:1; transform:translateY(0); }
  @media (max-width:640px){ .connector{ padding-left:2.9rem; } }
  .connector .badge{
    position:absolute;
    left:1.9rem; top:50%;
    transform:translate(-50%,-50%);
    width:26px; height:26px;
    border-radius:50%;
    background:var(--paper);
    border:1px solid var(--line);
    display:flex; align-items:center; justify-content:center;
    font-size:0.85rem;
    z-index:2;
  }
  @media (max-width:640px){ .connector .badge{ left:1.15rem; width:22px; height:22px; font-size:0.75rem; } }
  .connector-row{
    display:flex; align-items:center; justify-content:space-between; flex-wrap:wrap; gap:0.4rem 1rem;
  }
  .connector-row .leg{ font-size:0.86rem; color:var(--indigo-900); font-weight:600; }
  .connector-row .mode{ font-size:0.78rem; color:#5c5946; }
  .connector-row .figures{
    font-family:'JetBrains Mono', monospace;
    font-size:0.76rem;
    color:var(--kaki);
    white-space:nowrap;
  }

  .connector.flight .badge{ border-color:var(--indigo-700); }
  .connector.bike .badge{ border-color:var(--moss); background:var(--moss-soft); }

  /* budget */
  .budget{
    max-width:760px;
    margin:1rem auto 0;
    padding:0 1.5rem 5rem;
  }
  .budget h2{
    font-size:1.6rem;
    color:var(--indigo-900);
    margin-bottom:0.3rem;
  }
  .budget .lede{
    font-size:0.9rem; color:#4a4838; max-width:56ch; margin-bottom:1.6rem; line-height:1.55;
  }
  table.breakdown{
    width:100%;
    border-collapse:collapse;
    background:var(--paper-card);
    border:1px solid var(--line);
    box-shadow:var(--shadow);
  }
  table.breakdown th, table.breakdown td{
    padding:0.75rem 1rem;
    text-align:left;
    border-bottom:1px solid var(--paper-dim);
    font-size:0.85rem;
  }
  table.breakdown th{
    font-family:'JetBrains Mono', monospace;
    font-size:0.68rem;
    text-transform:uppercase;
    letter-spacing:0.08em;
    color:var(--indigo-700);
    background:var(--paper-dim);
  }
  table.breakdown td.amt{
    font-family:'JetBrains Mono', monospace;
    text-align:right;
    color:var(--indigo-900);
    font-weight:600;
  }
  table.breakdown tr:last-child td{ border-bottom:none; }
  table.breakdown tr.total td{
    font-weight:700;
    background:var(--paper-dim);
    border-top:2px solid var(--indigo-900);
  }
  table.breakdown tr.total td.amt{ color:var(--kaki); font-size:1rem; }

  .accor-note{
    margin-top:1.5rem;
    display:flex; gap:0.9rem; align-items:flex-start;
    padding:1rem 1.1rem;
    background:var(--indigo-900);
    color:var(--paper);
  }
  .accor-note .icon{ font-size:1.2rem; }
  .accor-note b{ color:var(--kaki-soft); }
  .accor-note p{ margin:0.25rem 0 0; font-size:0.85rem; line-height:1.55; color:rgba(243,236,217,0.85); }

  footer{
    max-width:760px; margin:0 auto; padding:0 1.5rem 3.5rem;
    font-size:0.76rem; color:#8a8570; line-height:1.6;
  }
  footer .rule{ height:1px; background:var(--line); margin-bottom:1.2rem; }
</style>
</head>
<body>

<div id="progress-rail"><div id="progress-fill"></div></div>

<div id="minibar">
  <span class="title">Okinawa → Tokyo</span>
  <span class="stats">
    <span>16 <b>nights</b></span>
    <span>8 <b>stops</b></span>
    <span>~$16k <b>AUD</b></span>
  </span>
</div>

<header class="hero">
  <div class="hero-inner">
    <div class="eyebrow">Kierin &amp; Becky · Oct 21 – Nov 6</div>
    <h1>Okinawa to Tokyo, <em>one line south to north.</em></h1>
    <p class="sub">Sixteen nights, eight stops, one bike ride across the Seto Inland Sea. Islands, onsen towns, a private hot spring facing Fuji, and five easy nights in Tokyo to finish.</p>
    <div class="for">PLANNING DOCUMENT — RATES ARE ESTIMATES, CONFIRM BEFORE BOOKING</div>
  </div>
</header>

<div class="stat-strip">
  <div class="stat"><div class="num">16</div><div class="label">Nights</div></div>
  <div class="stat"><div class="num">70km</div><div class="label">Cycled</div></div>
  <div class="stat"><div class="num">7</div><div class="label">Accor nights</div></div>
  <div class="stat"><div class="num">$15–17k</div><div class="label">Est. total AUD</div></div>
</div>

<main class="route">
  <div class="spine-line"></div>

  <!-- flight in -->
  <div class="connector flight reveal">
    <div class="badge">✈</div>
    <div class="connector-row">
      <div><span class="leg">Sydney → Naha</span> <span class="mode">· international flight</span></div>
      <div class="figures">~8–9 HRS · $900–1,400pp</div>
    </div>
  </div>

  <!-- 1 OKINAWA -->
  <div class="stop reveal">
    <div class="dot"></div>
    <div class="stop-card">
      <div class="stop-head">
        <span class="place">01 · Okinawa</span>
        <span class="dates">OCT 21 – 23</span>
      </div>
      <div class="hotel-name">Novotel Okinawa Naha</div>
      <p class="note">Infinity pool over the city, easy Kokusai-dori access. Two nights is enough for Shuri Castle, a beach afternoon and a proper Ryukyuan dinner without overstaying.</p>
      <div class="meta-row">
        <span class="chip">2 nights</span>
        <span class="chip rate">$130–180 / night</span>
        <span class="chip accor">ACCOR</span>
      </div>
    </div>
  </div>

  <div class="connector reveal">
    <div class="badge">✈</div>
    <div class="connector-row">
      <div><span class="leg">Naha → Fukuoka</span> <span class="mode">· domestic flight</span></div>
      <div class="figures">~1H35 · $150–250pp</div>
    </div>
  </div>

  <!-- 2 FUKUOKA -->
  <div class="stop reveal">
    <div class="dot"></div>
    <div class="stop-card">
      <div class="stop-head">
        <span class="place">02 · Fukuoka</span>
        <span class="dates">OCT 23 – 25</span>
      </div>
      <div class="hotel-name">The Ritz-Carlton, Fukuoka</div>
      <p class="note">Tenjin district, bay views, six dining venues. Best food city on the whole trip — yatai stalls, Hakata ramen, and a Dazaifu side trip if there's time.</p>
      <div class="meta-row">
        <span class="chip">2 nights</span>
        <span class="chip rate">$900–1,200 / night</span>
      </div>
    </div>
  </div>

  <div class="connector reveal">
    <div class="badge">🚆</div>
    <div class="connector-row">
      <div><span class="leg">Fukuoka → Beppu</span> <span class="mode">· JR Sonic Express</span></div>
      <div class="figures">~2H · $57pp</div>
    </div>
  </div>

  <!-- 3 BEPPU -->
  <div class="stop reveal">
    <div class="dot"></div>
    <div class="stop-card">
      <div class="stop-head">
        <span class="place">03 · Beppu</span>
        <span class="dates">OCT 25 – 27</span>
      </div>
      <div class="hotel-name">ANA InterContinental Beppu Resort &amp; Spa</div>
      <p class="note">Hillside over the bay with proper outdoor thermal pools. The best onsen city in Japan — this is the one to slow right down for.</p>
      <div class="meta-row">
        <span class="chip">2 nights</span>
        <span class="chip rate">$500–750 / night</span>
      </div>
    </div>
  </div>

  <div class="connector reveal">
    <div class="badge">🚆</div>
    <div class="connector-row">
      <div><span class="leg">Beppu → Onomichi</span> <span class="mode">· Sonic + Shinkansen</span></div>
      <div class="figures">~3–3.5H · $90–100pp</div>
    </div>
  </div>

  <!-- 4 ONOMICHI -->
  <div class="stop cycling reveal">
    <div class="dot"></div>
    <div class="stop-card">
      <div class="stop-head">
        <span class="place">04 · Onomichi</span>
        <span class="dates">OCT 27 – 28</span>
      </div>
      <div class="hotel-name">Hotel Cycle</div>
      <p class="note">Built for exactly this. Bike storage in the room, Shimano 105s to hire, ferry terminal on the doorstep. Ask for a window room.</p>
      <div class="meta-row">
        <span class="chip">1 night</span>
        <span class="chip rate">$180–250 / night</span>
        <span class="chip cyc">🚴 RIDE START</span>
      </div>
    </div>
  </div>

  <div class="connector bike reveal">
    <div class="badge">🚴</div>
    <div class="connector-row">
      <div><span class="leg">Onomichi → Setoda</span> <span class="mode">· Shimanami Kaido cycling</span></div>
      <div class="figures">~35KM · 2–3H · BIKE HIRE $40–60/DAY</div>
    </div>
  </div>

  <!-- 5 SETODA -->
  <div class="stop cycling reveal">
    <div class="dot"></div>
    <div class="stop-card">
      <div class="stop-head">
        <span class="place">05 · Ikuchi Island (Setoda)</span>
        <span class="dates">OCT 28 – 29</span>
      </div>
      <div class="hotel-name">Azumi Setoda</div>
      <p class="note">~35km into the ride. Boutique ryokan, onsen across the street, the best stay on the entire Shimanami route.</p>
      <div class="meta-row">
        <span class="chip">1 night</span>
        <span class="chip rate">$700–950 / night</span>
        <span class="chip cyc">🚴 35KM DONE</span>
      </div>
    </div>
  </div>

  <div class="connector bike reveal">
    <div class="badge">🚴</div>
    <div class="connector-row">
      <div><span class="leg">Setoda → Imabari → Kyoto</span> <span class="mode">· ride, then bus + Shinkansen via Okayama</span></div>
      <div class="figures">~35KM RIDE + 2.5–3H · $90–105pp</div>
    </div>
  </div>

  <!-- 6 KYOTO -->
  <div class="stop reveal">
    <div class="dot"></div>
    <div class="stop-card">
      <div class="stop-head">
        <span class="place">06 · Kyoto</span>
        <span class="dates">OCT 29 – 31</span>
      </div>
      <div class="hotel-name">Hotel The Mitsui Kyoto</div>
      <p class="note">Luxury Collection, built on 300-year-old grounds, tea ceremony on arrival. Worth stepping outside Accor for.</p>
      <div class="meta-row">
        <span class="chip">2 nights</span>
        <span class="chip rate">$1,100–1,500 / night</span>
      </div>
    </div>
  </div>

  <div class="connector reveal">
    <div class="badge">🚆</div>
    <div class="connector-row">
      <div><span class="leg">Kyoto → Kawaguchiko</span> <span class="mode">· Shinkansen + highway bus</span></div>
      <div class="figures">~3H · $95–110pp</div>
    </div>
  </div>

  <!-- 7 KAWAGUCHIKO -->
  <div class="stop reveal">
    <div class="dot"></div>
    <div class="stop-card">
      <div class="stop-head">
        <span class="place">07 · Kawaguchiko</span>
        <span class="dates">OCT 31 – NOV 1</span>
      </div>
      <div class="hotel-name">FuFu Kawaguchiko</div>
      <p class="note">Private in-room onsen facing Mt Fuji. Late October is one of the best windows for a clear view, with maple colour around the lake building toward peak.</p>
      <div class="meta-row">
        <span class="chip">1 night</span>
        <span class="chip rate">$900–1,300 / night</span>
      </div>
    </div>
  </div>

  <div class="connector reveal">
    <div class="badge">🚌</div>
    <div class="connector-row">
      <div><span class="leg">Kawaguchiko → Tokyo</span> <span class="mode">· highway bus, direct</span></div>
      <div class="figures">~1H50 · $22pp</div>
    </div>
  </div>

  <!-- 8 TOKYO -->
  <div class="stop reveal">
    <div class="dot"></div>
    <div class="stop-card">
      <div class="stop-head">
        <span class="place">08 · Tokyo</span>
        <span class="dates">NOV 1 – 6</span>
      </div>
      <div class="hotel-name">Fairmont Tokyo</div>
      <p class="note">35th floor and up, pool overlooking Tokyo Tower. Five nights at the end means no rush — proper shopping, a couple of splurge dinners, one completely loose day.</p>
      <div class="meta-row">
        <span class="chip">5 nights</span>
        <span class="chip rate">$650–900 / night</span>
        <span class="chip accor">ACCOR</span>
      </div>
      <div class="side-trip">
        <div class="icon">🚆</div>
        <div class="txt">
          <b>Day trip — Kamakura &amp; Enoshima</b>
          <span>~1hr each way by JR. Great Buddha, Hase-dera, bamboo groves at Hokoku-ji, then sunset over the water at Enoshima. Round trip ~$19–22pp — day trip, not worth an overnight.</span>
        </div>
      </div>
    </div>
  </div>

  <div class="connector flight reveal">
    <div class="badge">✈</div>
    <div class="connector-row">
      <div><span class="leg">Tokyo → Sydney</span> <span class="mode">· international flight</span></div>
      <div class="figures">~9–10H · PAIRED W/ OUTBOUND</div>
    </div>
  </div>

</main>

<section class="budget">
  <h2>Budget summary</h2>
  <p class="lede">Estimates only — hotel rates swing with room type and season, and October–November is peak. Confirm actual prices as you book, especially Azumi Setoda and FuFu Kawaguchiko, which have few rooms and sell out early.</p>
  <table class="breakdown">
    <thead>
      <tr><th>Category</th><th style="text-align:right">Estimate (AUD)</th></tr>
    </thead>
    <tbody>
      <tr><td>Hotels — 16 nights, 1 room</td><td class="amt">~$12,300</td></tr>
      <tr><td>Domestic transit &amp; bike hire (× 2 people)</td><td class="amt">~$1,150–1,460</td></tr>
      <tr><td>International flights (× 2 people)</td><td class="amt">~$1,800–2,800</td></tr>
      <tr class="total"><td>Rough trip total</td><td class="amt">~$15,250–16,560</td></tr>
    </tbody>
  </table>

  <div class="accor-note">
    <div class="icon">◆</div>
    <div>
      <b>7 Accor nights on this trip</b>
      <p>Novotel Okinawa Naha (2 nights) and Fairmont Tokyo (5 nights) — both the right hotel on merit, not just for status. Check ALL member rates on both before booking through a third party; Fairmont sometimes runs longer-stay offers.</p>
    </div>
  </div>
</section>

<footer>
  <div class="rule"></div>
  Built as a shared planning reference — dates, hotels and prices to be locked in as bookings are confirmed. Last updated for a departure of Oct 21, arrival home Nov 6.
</footer>

<script>
  // scroll progress
  const fill = document.getElementById('progress-fill');
  function updateProgress(){
    const h = document.documentElement;
    const scrolled = h.scrollTop;
    const height = h.scrollHeight - h.clientHeight;
    const pct = height > 0 ? (scrolled / height) * 100 : 0;
    fill.style.height = pct + '%';
  }
  document.addEventListener('scroll', updateProgress, { passive:true });
  updateProgress();

  // reveal on scroll
  const els = document.querySelectorAll('.reveal, .stop, .connector');
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{
      if(e.isIntersecting){
        e.target.classList.add('in');
        io.unobserve(e.target);
      }
    });
  }, { threshold:0.12, rootMargin:'0px 0px -8% 0px' });
  els.forEach(el=>io.observe(el));
</script>

</body>
</html>
