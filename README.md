<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bresse Factory – Véhicules d'Occasion</title>
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;600;700;800;900&family=Barlow:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #F5C518;
    --gold-dark: #D4A017;
    --black: #111111;
    --dark: #1a1a1a;
    --dark2: #222222;
    --gray: #888;
    --light: #f5f5f0;
    --white: #ffffff;
    --red: #e63030;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'Barlow', sans-serif;
    background: var(--black);
    color: var(--white);
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; width: 100%; z-index: 100;
    background: rgba(10,10,10,0.95);
    backdrop-filter: blur(10px);
    border-bottom: 2px solid var(--gold);
    padding: 0 2rem;
    display: flex; align-items: center; justify-content: space-between;
    height: 70px;
  }
  .nav-logo img { height: 52px; }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 600; font-size: 1rem;
    color: var(--white); text-decoration: none;
    letter-spacing: 0.05em; text-transform: uppercase;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--gold); }
  .nav-cta {
    background: var(--gold); color: var(--black) !important;
    padding: 0.5rem 1.2rem; border-radius: 4px; font-weight: 700 !important;
  }
  .nav-cta:hover { background: var(--gold-dark); color: var(--black) !important; }
  .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
  .hamburger span { width: 26px; height: 2px; background: var(--white); display: block; }

  /* HERO */
  .hero {
    min-height: 100vh;
    background: linear-gradient(135deg, #0a0a0a 0%, #1a1a0a 50%, #0a0a0a 100%);
    display: flex; align-items: center; justify-content: center;
    position: relative; overflow: hidden;
    padding-top: 70px;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='60' height='60'%3E%3Cpath d='M0 60 L60 0' stroke='%23F5C51810' stroke-width='1'/%3E%3C/svg%3E");
  }
  .hero-stripe {
    position: absolute; bottom: 0; left: 0; right: 0; height: 6px;
    background: repeating-linear-gradient(90deg, var(--gold) 0, var(--gold) 30px, var(--black) 30px, var(--black) 60px);
  }
  .hero-content { text-align: center; z-index: 1; padding: 2rem; max-width: 900px; }
  .hero-badge {
    display: inline-block;
    background: var(--gold); color: var(--black);
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 800; font-size: 0.75rem; letter-spacing: 0.2em;
    text-transform: uppercase; padding: 0.4rem 1rem;
    border-radius: 2px; margin-bottom: 1.5rem;
  }
  .hero h1 {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900; font-size: clamp(3rem, 8vw, 6rem);
    line-height: 1; text-transform: uppercase;
    margin-bottom: 1rem;
  }
  .hero h1 span { color: var(--gold); display: block; }
  .hero p {
    font-size: 1.2rem; color: #bbb; max-width: 600px;
    margin: 0 auto 2.5rem;
  }
  .hero-btns { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
  .btn-primary {
    background: var(--gold); color: var(--black);
    font-family: 'Barlow Condensed', sans-serif; font-weight: 800;
    font-size: 1rem; letter-spacing: 0.1em; text-transform: uppercase;
    padding: 1rem 2.5rem; border-radius: 4px;
    text-decoration: none; transition: all 0.2s;
    border: 2px solid var(--gold);
  }
  .btn-primary:hover { background: var(--gold-dark); border-color: var(--gold-dark); transform: translateY(-2px); }
  .btn-outline {
    background: transparent; color: var(--white);
    font-family: 'Barlow Condensed', sans-serif; font-weight: 700;
    font-size: 1rem; letter-spacing: 0.1em; text-transform: uppercase;
    padding: 1rem 2.5rem; border-radius: 4px;
    text-decoration: none; transition: all 0.2s;
    border: 2px solid rgba(255,255,255,0.3);
  }
  .btn-outline:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-2px); }

  /* STATS */
  .stats {
    background: var(--gold);
    padding: 3rem 2rem;
  }
  .stats-grid {
    max-width: 900px; margin: 0 auto;
    display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 2rem; text-align: center;
  }
  .stat-num {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900; font-size: 3rem; color: var(--black); line-height: 1;
  }
  .stat-label {
    font-size: 0.85rem; font-weight: 600; color: rgba(0,0,0,0.65);
    text-transform: uppercase; letter-spacing: 0.1em;
    margin-top: 0.3rem;
  }

  /* SECTION */
  section { padding: 5rem 2rem; }
  .section-tag {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 700; font-size: 0.8rem; letter-spacing: 0.3em;
    text-transform: uppercase; color: var(--gold);
    margin-bottom: 0.75rem; display: block;
  }
  .section-title {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900; font-size: clamp(2rem, 5vw, 3.5rem);
    text-transform: uppercase; line-height: 1.05;
  }
  .section-sub {
    color: var(--gray); font-size: 1rem; margin-top: 0.75rem; max-width: 500px;
  }
  .section-header { margin-bottom: 3rem; }
  .container { max-width: 1100px; margin: 0 auto; }

  /* VEHICULES */
  #vehicules { background: var(--dark); }
  .cars-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem;
  }
  .car-card {
    background: var(--dark2);
    border-radius: 8px;
    overflow: hidden;
    border: 1px solid rgba(255,255,255,0.06);
    transition: transform 0.2s, border-color 0.2s;
  }
  .car-card:hover { transform: translateY(-4px); border-color: var(--gold); }
  .car-img {
    height: 200px; background: #2a2a2a;
    display: flex; align-items: center; justify-content: center;
    font-size: 4rem; position: relative; overflow: hidden;
  }
  .car-img svg { width: 120px; opacity: 0.5; }
  .car-badge-new {
    position: absolute; top: 12px; left: 12px;
    background: var(--gold); color: var(--black);
    font-family: 'Barlow Condensed', sans-serif; font-weight: 800;
    font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase;
    padding: 0.25rem 0.6rem; border-radius: 3px;
  }
  .car-badge-vendu {
    position: absolute; top: 12px; left: 12px;
    background: var(--red); color: var(--white);
    font-family: 'Barlow Condensed', sans-serif; font-weight: 800;
    font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase;
    padding: 0.25rem 0.6rem; border-radius: 3px;
  }
  .car-info { padding: 1.25rem; }
  .car-make {
    font-size: 0.75rem; font-weight: 600; color: var(--gold);
    text-transform: uppercase; letter-spacing: 0.1em;
  }
  .car-name {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 800; font-size: 1.4rem; text-transform: uppercase;
    margin: 0.2rem 0 0.75rem;
  }
  .car-specs { display: flex; gap: 1rem; flex-wrap: wrap; margin-bottom: 1rem; }
  .car-spec {
    font-size: 0.8rem; color: var(--gray);
    display: flex; align-items: center; gap: 0.3rem;
  }
  .car-spec::before { content: '•'; color: var(--gold); }
  .car-footer {
    display: flex; justify-content: space-between; align-items: center;
    padding-top: 1rem; border-top: 1px solid rgba(255,255,255,0.08);
  }
  .car-price {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900; font-size: 1.6rem; color: var(--gold);
  }
  .car-price span { font-size: 1rem; font-weight: 600; }
  .car-btn {
    font-family: 'Barlow Condensed', sans-serif; font-weight: 700;
    font-size: 0.85rem; letter-spacing: 0.08em; text-transform: uppercase;
    color: var(--black); background: var(--gold);
    padding: 0.5rem 1.1rem; border-radius: 4px;
    text-decoration: none; transition: background 0.2s;
  }
  .car-btn:hover { background: var(--gold-dark); }
  .vendu-overlay { opacity: 0.5; pointer-events: none; }
  .cars-cta { text-align: center; margin-top: 3rem; }
  .cars-note { font-size: 0.9rem; color: var(--gray); margin-top: 1rem; }

  /* SERVICES */
  #services { background: var(--black); }
  .services-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1.5rem;
  }
  .service-card {
    background: var(--dark2);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 8px; padding: 2rem;
    transition: border-color 0.2s;
  }
  .service-card:hover { border-color: var(--gold); }
  .service-icon {
    width: 52px; height: 52px;
    background: rgba(245,197,24,0.12);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    margin-bottom: 1.25rem;
  }
  .service-icon svg { width: 26px; height: 26px; fill: var(--gold); }
  .service-card h3 {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 800; font-size: 1.2rem; text-transform: uppercase;
    margin-bottom: 0.6rem;
  }
  .service-card p { font-size: 0.9rem; color: var(--gray); line-height: 1.7; }

  /* ABOUT */
  #about {
    background: var(--dark);
  }
  .about-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 4rem; align-items: center;
  }
  .about-text .section-sub { max-width: 100%; margin-top: 1rem; line-height: 1.8; }
  .about-list { list-style: none; margin-top: 1.5rem; display: flex; flex-direction: column; gap: 0.75rem; }
  .about-list li {
    display: flex; align-items: center; gap: 0.75rem;
    font-size: 0.95rem; color: #ccc;
  }
  .about-list li::before {
    content: ''; width: 6px; height: 6px; background: var(--gold);
    border-radius: 50%; flex-shrink: 0;
  }
  .about-visual {
    background: var(--dark2);
    border: 1px solid rgba(245,197,24,0.2);
    border-radius: 8px; padding: 2.5rem;
    text-align: center;
  }
  .about-visual img { width: 100%; max-width: 300px; }
  .about-quote {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 700; font-size: 1.3rem; text-transform: uppercase;
    color: var(--gold); margin-top: 1.5rem; line-height: 1.3;
  }

  /* CONTACT */
  #contact { background: var(--black); }
  .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; }
  .contact-info { display: flex; flex-direction: column; gap: 1.5rem; margin-top: 1rem; }
  .contact-item {
    display: flex; align-items: flex-start; gap: 1rem;
  }
  .contact-icon {
    width: 44px; height: 44px; flex-shrink: 0;
    background: rgba(245,197,24,0.12); border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
  }
  .contact-icon svg { width: 20px; height: 20px; fill: var(--gold); }
  .contact-item-label { font-size: 0.75rem; color: var(--gray); text-transform: uppercase; letter-spacing: 0.1em; }
  .contact-item-val { font-size: 1rem; font-weight: 500; margin-top: 0.2rem; }
  .contact-item-val a { color: var(--white); text-decoration: none; }
  .contact-item-val a:hover { color: var(--gold); }
  .contact-form { display: flex; flex-direction: column; gap: 1rem; }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
  .form-group { display: flex; flex-direction: column; gap: 0.4rem; }
  .form-group label { font-size: 0.8rem; color: var(--gray); text-transform: uppercase; letter-spacing: 0.08em; }
  .form-group input, .form-group textarea, .form-group select {
    background: var(--dark2); border: 1px solid rgba(255,255,255,0.1);
    color: var(--white); border-radius: 6px;
    padding: 0.75rem 1rem; font-size: 0.95rem; font-family: 'Barlow', sans-serif;
    transition: border-color 0.2s; resize: vertical;
  }
  .form-group select option { background: var(--dark2); }
  .form-group input:focus, .form-group textarea:focus, .form-group select:focus {
    outline: none; border-color: var(--gold);
  }
  .form-submit {
    background: var(--gold); color: var(--black);
    font-family: 'Barlow Condensed', sans-serif; font-weight: 800;
    font-size: 1rem; letter-spacing: 0.1em; text-transform: uppercase;
    padding: 1rem; border: none; border-radius: 6px;
    cursor: pointer; transition: background 0.2s;
  }
  .form-submit:hover { background: var(--gold-dark); }
  .form-success {
    display: none; background: rgba(99,201,70,0.1); border: 1px solid rgba(99,201,70,0.3);
    border-radius: 6px; padding: 1rem; text-align: center;
    color: #6fca46; font-weight: 600;
  }

  /* FOOTER */
  footer {
    background: var(--dark);
    border-top: 2px solid var(--gold);
    padding: 3rem 2rem 2rem;
  }
  .footer-inner {
    max-width: 1100px; margin: 0 auto;
    display: grid; grid-template-columns: 2fr 1fr 1fr; gap: 3rem;
  }
  .footer-logo img { height: 50px; margin-bottom: 1rem; }
  .footer-desc { font-size: 0.9rem; color: var(--gray); line-height: 1.7; max-width: 280px; }
  .footer-col h4 {
    font-family: 'Barlow Condensed', sans-serif; font-weight: 800;
    font-size: 1rem; text-transform: uppercase; letter-spacing: 0.1em;
    color: var(--gold); margin-bottom: 1rem;
  }
  .footer-col ul { list-style: none; display: flex; flex-direction: column; gap: 0.5rem; }
  .footer-col ul a { color: var(--gray); text-decoration: none; font-size: 0.9rem; transition: color 0.2s; }
  .footer-col ul a:hover { color: var(--white); }
  .footer-bottom {
    max-width: 1100px; margin: 2.5rem auto 0;
    padding-top: 1.5rem; border-top: 1px solid rgba(255,255,255,0.08);
    display: flex; justify-content: space-between; align-items: center;
    flex-wrap: wrap; gap: 1rem;
    font-size: 0.8rem; color: var(--gray);
  }

  /* WHATSAPP FAB */
  .whatsapp-fab {
    position: fixed; bottom: 2rem; right: 2rem; z-index: 99;
    width: 58px; height: 58px; border-radius: 50%;
    background: #25D366;
    display: flex; align-items: center; justify-content: center;
    box-shadow: 0 4px 20px rgba(37,211,102,0.4);
    text-decoration: none; transition: transform 0.2s;
  }
  .whatsapp-fab:hover { transform: scale(1.1); }
  .whatsapp-fab svg { width: 32px; height: 32px; fill: white; }

  /* RESPONSIVE */
  @media (max-width: 768px) {
    .nav-links { display: none; }
    .hamburger { display: flex; }
    .nav-links.open {
      display: flex; flex-direction: column;
      position: fixed; top: 70px; left: 0; right: 0;
      background: rgba(10,10,10,0.98);
      padding: 2rem; gap: 1.5rem;
    }
    .about-grid, .contact-grid { grid-template-columns: 1fr; gap: 2rem; }
    .footer-inner { grid-template-columns: 1fr; gap: 2rem; }
    .form-row { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">
    <img src="LOGO_BRESSE_FACTORY_FINAL.png" alt="Bresse Factory" onerror="this.style.display='none'; this.nextElementSibling.style.display='block'">
    <span style="display:none; font-family:'Barlow Condensed',sans-serif; font-weight:900; font-size:1.4rem; color:var(--gold);">BRESSE FACTORY</span>
  </div>
  <ul class="nav-links" id="navLinks">
    <li><a href="#vehicules">Véhicules</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#about">À propos</a></li>
    <li><a href="#contact" class="nav-cta">Nous contacter</a></li>
  </ul>
  <div class="hamburger" onclick="toggleMenu()">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-content">
    <div class="hero-badge">&#9660; Véhicules d'occasion — Bresse &amp; alentours</div>
    <h1>Votre prochain<span>véhicule</span>vous attend</h1>
    <p>Des véhicules soigneusement sélectionnés, un service de proximité et des prix honnêtes. Bienvenue chez Bresse Factory.</p>
    <div class="hero-btns">
      <a href="#vehicules" class="btn-primary">Voir les véhicules</a>
      <a href="#contact" class="btn-outline">Prendre contact</a>
    </div>
  </div>
  <div class="hero-stripe"></div>
</section>

<!-- STATS -->
<div class="stats">
  <div class="stats-grid">
    <div>
      <div class="stat-num">100%</div>
      <div class="stat-label">Véhicules contrôlés</div>
    </div>
    <div>
      <div class="stat-num">0€</div>
      <div class="stat-label">Frais cachés</div>
    </div>
    <div>
      <div class="stat-num">Local</div>
      <div class="stat-label">Ancré dans la Bresse</div>
    </div>
    <div>
      <div class="stat-num">Pro</div>
      <div class="stat-label">Micro-entreprise déclarée</div>
    </div>
  </div>
</div>

<!-- VÉHICULES -->
<section id="vehicules">
  <div class="container">
    <div class="section-header">
      <span class="section-tag">Stock disponible</span>
      <h2 class="section-title">Nos véhicules</h2>
      <p class="section-sub">Chaque véhicule est inspecté avant mise en vente. Financement possible selon partenaires.</p>
    </div>
    <div class="cars-grid">

      <!-- Exemple véhicule 1 -->
      <div class="car-card">
        <div class="car-img">
          <div class="car-badge-new">Nouveau</div>
          <svg viewBox="0 0 100 50" xmlns="http://www.w3.org/2000/svg">
            <rect x="5" y="20" width="90" height="22" rx="6" fill="#444"/>
            <rect x="20" y="10" width="55" height="18" rx="5" fill="#555"/>
            <circle cx="22" cy="44" r="8" fill="#333" stroke="#666" stroke-width="2"/>
            <circle cx="78" cy="44" r="8" fill="#333" stroke="#666" stroke-width="2"/>
            <circle cx="22" cy="44" r="4" fill="#888"/>
            <circle cx="78" cy="44" r="4" fill="#888"/>
          </svg>
        </div>
        <div class="car-info">
          <div class="car-make">Renault</div>
          <div class="car-name">Clio V 1.0 TCe</div>
          <div class="car-specs">
            <span class="car-spec">2021</span>
            <span class="car-spec">45 000 km</span>
            <span class="car-spec">Essence</span>
            <span class="car-spec">5 portes</span>
          </div>
          <div class="car-footer">
            <div class="car-price">11 500<span> €</span></div>
            <a href="#contact" class="car-btn">Renseignement</a>
          </div>
        </div>
      </div>

      <!-- Exemple véhicule 2 -->
      <div class="car-card">
        <div class="car-img">
          <svg viewBox="0 0 100 50" xmlns="http://www.w3.org/2000/svg">
            <rect x="5" y="18" width="90" height="24" rx="5" fill="#444"/>
            <rect x="15" y="8" width="60" height="18" rx="4" fill="#555"/>
            <circle cx="22" cy="44" r="8" fill="#333" stroke="#666" stroke-width="2"/>
            <circle cx="78" cy="44" r="8" fill="#333" stroke="#666" stroke-width="2"/>
            <circle cx="22" cy="44" r="4" fill="#888"/>
            <circle cx="78" cy="44" r="4" fill="#888"/>
          </svg>
        </div>
        <div class="car-info">
          <div class="car-make">Peugeot</div>
          <div class="car-name">308 SW 1.5 BlueHDi</div>
          <div class="car-specs">
            <span class="car-spec">2019</span>
            <span class="car-spec">78 000 km</span>
            <span class="car-spec">Diesel</span>
            <span class="car-spec">Break</span>
          </div>
          <div class="car-footer">
            <div class="car-price">14 900<span> €</span></div>
            <a href="#contact" class="car-btn">Renseignement</a>
          </div>
        </div>
      </div>

      <!-- Exemple véhicule 3 — Vendu -->
      <div class="car-card">
        <div class="car-img vendu-overlay">
          <div class="car-badge-vendu">Vendu</div>
          <svg viewBox="0 0 100 50" xmlns="http://www.w3.org/2000/svg">
            <rect x="5" y="22" width="90" height="20" rx="7" fill="#444"/>
            <rect x="25" y="12" width="45" height="16" rx="4" fill="#555"/>
            <circle cx="22" cy="44" r="8" fill="#333" stroke="#666" stroke-width="2"/>
            <circle cx="78" cy="44" r="8" fill="#333" stroke="#666" stroke-width="2"/>
            <circle cx="22" cy="44" r="4" fill="#888"/>
            <circle cx="78" cy="44" r="4" fill="#888"/>
          </svg>
        </div>
        <div class="car-info vendu-overlay">
          <div class="car-make">Volkswagen</div>
          <div class="car-name">Golf VII 1.6 TDI</div>
          <div class="car-specs">
            <span class="car-spec">2018</span>
            <span class="car-spec">92 000 km</span>
            <span class="car-spec">Diesel</span>
          </div>
          <div class="car-footer">
            <div class="car-price">13 200<span> €</span></div>
            <span style="font-size:0.85rem; color:var(--red); font-weight:700; text-transform:uppercase; letter-spacing:0.05em;">Vendu</span>
          </div>
        </div>
      </div>

    </div>
    <div class="cars-cta">
      <a href="#contact" class="btn-primary">Demander un véhicule spécifique</a>
      <p class="cars-note">Nouveau stock régulièrement. Contactez-nous pour être alerté.</p>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="container">
    <div class="section-header">
      <span class="section-tag">Ce qu'on propose</span>
      <h2 class="section-title">Nos services</h2>
    </div>
    <div class="services-grid">
      <div class="service-card">
        <div class="service-icon">
          <svg viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 14.5v-9l6 4.5-6 4.5z"/></svg>
        </div>
        <h3>Vente de véhicules d'occasion</h3>
        <p>Voitures soigneusement sélectionnées, contrôlées et proposées à des prix justes, sans commission excessive.</p>
      </div>
      <div class="service-card">
        <div class="service-icon">
          <svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 14H4V6h16v12zM6 10h2v2H6zm0 4h8v2H6zm10 0h2v2h-2zm-6-4h8v2h-8z"/></svg>
        </div>
        <h3>Accompagnement & conseil</h3>
        <p>On vous guide dans votre choix selon votre budget, vos besoins et votre usage. Pas de pression, juste du conseil honnête.</p>
      </div>
      <div class="service-card">
        <div class="service-icon">
          <svg viewBox="0 0 24 24"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-7 3c1.93 0 3.5 1.57 3.5 3.5S13.93 13 12 13s-3.5-1.57-3.5-3.5S10.07 6 12 6zm7 13H5v-.23c0-.62.28-1.2.76-1.58C7.47 15.82 9.64 15 12 15s4.53.82 6.24 2.19c.48.38.76.97.76 1.58V19z"/></svg>
        </div>
        <h3>Service de proximité</h3>
        <p>Une micro-entreprise locale, disponible, réactive. Vous avez un interlocuteur unique du début à la fin.</p>
      </div>
      <div class="service-card">
        <div class="service-icon">
          <svg viewBox="0 0 24 24"><path d="M3 13h8V3H3v10zm0 8h8v-6H3v6zm10 0h8V11h-8v10zm0-18v6h8V3h-8z"/></svg>
        </div>
        <h3>Recherche sur mesure</h3>
        <p>Vous cherchez un modèle précis ? Dites-nous ce que vous voulez, on s'occupe de trouver la perle rare pour vous.</p>
      </div>
    </div>
  </div>
</section>

<!-- À PROPOS -->
<section id="about">
  <div class="container">
    <div class="about-grid">
      <div class="about-text">
        <span class="section-tag">Qui sommes-nous</span>
        <h2 class="section-title">Bresse Factory,<br>une passion, un métier</h2>
        <p class="section-sub">Née de la passion de l'automobile, Bresse Factory est une micro-entreprise implantée en Bresse qui met le client au cœur de chaque transaction. Ici, pas de grande enseigne, pas de vendeur sous pression — juste quelqu'un qui aime les voitures et veut vous aider à trouver la bonne.</p>
        <ul class="about-list">
          <li>Micro-entreprise déclarée, transparent sur les prix</li>
          <li>Véhicules contrôlés avant chaque vente</li>
          <li>Suivi personnalisé, disponible 7j/7</li>
          <li>Ancré dans la région Bresse / Ain / Saône-et-Loire</li>
          <li>Carte grise et démarches administratives facilitées</li>
        </ul>
      </div>
      <div class="about-visual">
        <img src="LOGO_BRESSE_FACTORY_FINAL.png" alt="Bresse Factory" onerror="this.style.display='none'">
        <div class="about-quote">"La bonne voiture,<br>au bon prix,<br>près de chez vous."</div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="container">
    <div class="section-header">
      <span class="section-tag">Parlons-en</span>
      <h2 class="section-title">Nous contacter</h2>
      <p class="section-sub">Une question sur un véhicule ? Envie de nous soumettre une recherche ? On vous répond rapidement.</p>
    </div>
    <div class="contact-grid">
      <div>
        <div class="contact-info">
          <div class="contact-item">
            <div class="contact-icon">
              <svg viewBox="0 0 24 24"><path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/></svg>
            </div>
            <div>
              <div class="contact-item-label">Téléphone / WhatsApp</div>
              <div class="contact-item-val"><a href="tel:+33600000000">06 00 00 00 00</a></div>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">
              <svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
            </div>
            <div>
              <div class="contact-item-label">Email</div>
              <div class="contact-item-val"><a href="mailto:contact@bressefactory.fr">contact@bressefactory.fr</a></div>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">
              <svg viewBox="0 0 24 24"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/></svg>
            </div>
            <div>
              <div class="contact-item-label">Zone</div>
              <div class="contact-item-val">Bresse — Ain / Saône-et-Loire</div>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">
              <svg viewBox="0 0 24 24"><path d="M11.99 2C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zM12 20c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8zm.5-13H11v6l5.25 3.15.75-1.23-4.5-2.67V7z"/></svg>
            </div>
            <div>
              <div class="contact-item-label">Disponibilité</div>
              <div class="contact-item-val">Lun–Sam · 9h–19h</div>
            </div>
          </div>
        </div>
      </div>
      <div>
        <div class="contact-form">
          <div class="form-row">
            <div class="form-group">
              <label>Prénom</label>
              <input type="text" id="fname" placeholder="Jean">
            </div>
            <div class="form-group">
              <label>Nom</label>
              <input type="text" id="lname" placeholder="Dupont">
            </div>
          </div>
          <div class="form-group">
            <label>Téléphone</label>
            <input type="tel" id="phone" placeholder="06 12 34 56 78">
          </div>
          <div class="form-group">
            <label>Sujet</label>
            <select id="subject">
              <option value="">-- Choisir --</option>
              <option>Renseignement sur un véhicule</option>
              <option>Recherche de véhicule</option>
              <option>Proposition de reprise</option>
              <option>Autre</option>
            </select>
          </div>
          <div class="form-group">
            <label>Message</label>
            <textarea id="message" rows="4" placeholder="Dites-nous ce que vous cherchez..."></textarea>
          </div>
          <button class="form-submit" onclick="submitForm()">Envoyer le message &rarr;</button>
          <div class="form-success" id="formSuccess">
            ✓ Votre message a été envoyé. On vous répond très vite !
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div>
      <div class="footer-logo">
        <img src="LOGO_BRESSE_FACTORY_FINAL.png" alt="Bresse Factory" onerror="this.style.display='none'; this.nextElementSibling.style.display='block'">
        <span style="display:none; font-family:'Barlow Condensed',sans-serif; font-weight:900; font-size:1.6rem; color:var(--gold);">BRESSE FACTORY</span>
      </div>
      <p class="footer-desc">Votre spécialiste local de la vente de véhicules d'occasion en Bresse. Micro-entreprise, prix transparents, service humain.</p>
    </div>
    <div class="footer-col">
      <h4>Navigation</h4>
      <ul>
        <li><a href="#vehicules">Nos véhicules</a></li>
        <li><a href="#services">Services</a></li>
        <li><a href="#about">À propos</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Contact</h4>
      <ul>
        <li><a href="tel:+33600000000">06 00 00 00 00</a></li>
        <li><a href="mailto:contact@bressefactory.fr">contact@bressefactory.fr</a></li>
        <li><a href="#">Bresse — 01 / 71</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2025 Bresse Factory — Micro-entreprise</span>
    <span>Site réalisé localement · Mentions légales</span>
  </div>
</footer>

<!-- WhatsApp FAB -->
<a href="https://wa.me/33600000000" class="whatsapp-fab" target="_blank" title="Nous contacter sur WhatsApp">
  <svg viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.025.507 3.934 1.395 5.608L0 24l6.562-1.374A11.943 11.943 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.818a9.818 9.818 0 01-5.001-1.372l-.36-.213-3.714.778.793-3.625-.234-.372A9.818 9.818 0 012.182 12C2.182 6.565 6.565 2.182 12 2.182S21.818 6.565 21.818 12 17.435 21.818 12 21.818z"/></svg>
</a>

<script>
function toggleMenu() {
  document.getElementById('navLinks').classList.toggle('open');
}
function submitForm() {
  const fname = document.getElementById('fname').value;
  const phone = document.getElementById('phone').value;
  const subject = document.getElementById('subject').value;
  const message = document.getElementById('message').value;
  if (!fname || !phone || !message) {
    alert('Merci de remplir au moins votre prénom, téléphone et message.');
    return;
  }
  document.getElementById('formSuccess').style.display = 'block';
  document.querySelector('.form-submit').style.display = 'none';
}
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
  anchor.addEventListener('click', function(e) {
    e.preventDefault();
    document.getElementById('navLinks').classList.remove('open');
    document.querySelector(this.getAttribute('href')).scrollIntoView({ behavior: 'smooth' });
  });
});
</script>
</body>
</html>
