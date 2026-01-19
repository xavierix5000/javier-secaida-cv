<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CV - Javier Secaida | Community Manager</title>
    <style>
        :root {
            /* Palette inspired by Meta Business Suite / Dashboard */
            --bg-body: #F0F2F5;
            --sidebar-bg: #FFFFFF;
            --card-bg: rgba(255, 255, 255, 0.85);
            --primary: #1877F2; /* Meta Blue */
            --text-dark: #1C1E21;
            --text-gray: #65676B;
            --text-light: #B0B3B8;
            --green-trend: #31A24C;
            --orange-trend: #F7B928;
            --purple-accent: #8E2DE2;
            --glass-border: 1px solid rgba(255, 255, 255, 0.4); 
            --shadow-sm: 0 2px 4px rgba(0,0,0,0.05);
            --shadow-md: 0 8px 16px rgba(0,0,0,0.06);
            --radius-lg: 16px;
            --radius-md: 12px;
            --font-main: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: var(--font-main);
            background: linear-gradient(135deg, #EBF4FF 0%, #F5F7FA 100%);
            color: var(--text-dark);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            padding: 20px;
            overflow: hidden; /* Prevent body scroll, content scrolls if needed */
        }

        /* Print Settings to ensure A4/Letter export looks like the design */
        @media print {
            @page { margin: 0; size: letter portrait; }
            body { 
                padding: 0; 
                height: auto; 
                background: #fff;
                -webkit-print-color-adjust: exact; 
                print-color-adjust: exact;
            }
            .cv-container {
                box-shadow: none;
                height: 100%;
                border-radius: 0;
                overflow: visible;
            }
            /* Adjust shadows for print readability */
            .card, .sidebar, .right-panel {
                box-shadow: none !important;
                border: 1px solid #ddd;
            }
        }

        /* Main Container */
        .cv-container {
            width: 100%;
            max-width: 1200px;
            height: 95vh; /* Fit in view */
            background: rgba(255, 255, 255, 0.6);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-radius: 24px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.1);
            display: grid;
            grid-template-columns: 260px 1fr 300px; /* Sidebar | Main | Right */
            gap: 20px;
            padding: 20px;
            border: var(--glass-border);
            position: relative;
        }

        /* --- LEFT SIDEBAR --- */
        .sidebar {
            background: var(--sidebar-bg);
            border-radius: var(--radius-lg);
            padding: 24px;
            display: flex;
            flex-direction: column;
            gap: 20px;
            box-shadow: var(--shadow-sm);
            height: 100%;
            overflow-y: auto;
        }

        .profile-header {
            text-align: center;
            margin-bottom: 10px;
        }

        .avatar-ring {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            padding: 3px;
            background: linear-gradient(45deg, #1877F2, #8E2DE2);
            margin: 0 auto 12px;
            position: relative;
        }

        .avatar-img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid #fff;
            background-color: #ddd;
        }

        .status-dot {
            position: absolute;
            bottom: 5px;
            right: 5px;
            width: 18px;
            height: 18px;
            background: #31A24C;
            border: 3px solid #fff;
            border-radius: 50%;
        }

        .profile-name {
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 4px;
        }

        .profile-role {
            font-size: 0.85rem;
            color: var(--text-gray);
            line-height: 1.3;
        }

        .contact-info {
            background: #F7F8FA;
            padding: 12px;
            border-radius: var(--radius-md);
            font-size: 0.8rem;
        }

        .contact-row {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 8px;
            color: var(--text-gray);
        }

        .contact-row:last-child { margin-bottom: 0; }
        .contact-row svg { width: 16px; height: 16px; fill: var(--primary); }

        .nav-menu {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .nav-item {
            display: flex;
            align-items: center;
            padding: 10px 12px;
            border-radius: 8px;
            color: var(--text-gray);
            font-weight: 500;
            cursor: default;
            transition: 0.2s;
            font-size: 0.9rem;
        }

        .nav-item.active {
            background: #EBF4FF;
            color: var(--primary);
        }

        .nav-item svg {
            margin-right: 12px;
            width: 20px;
            height: 20px;
            fill: currentColor;
        }

        .sidebar-footer {
            margin-top: auto;
            text-align: center;
        }

        .btn-ref {
            width: 100%;
            padding: 10px;
            background: linear-gradient(90deg, #1877F2, #4991f8);
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            font-size: 0.85rem;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(24, 119, 242, 0.3);
        }

        /* --- MIDDLE CONTENT --- */
        .main-content {
            display: flex;
            flex-direction: column;
            gap: 20px;
            overflow-y: auto; /* Allow scroll within this section */
            padding-right: 5px;
        }

        .search-bar-sim {
            background: var(--sidebar-bg);
            padding: 12px 20px;
            border-radius: 50px;
            display: flex;
            align-items: center;
            box-shadow: var(--shadow-sm);
            color: var(--text-gray);
            font-size: 0.9rem;
        }

        .hero-card {
            background: linear-gradient(120deg, #ffffff 0%, #f0f6ff 100%);
            border-radius: var(--radius-lg);
            padding: 24px;
            box-shadow: var(--shadow-sm);
            position: relative;
            overflow: hidden;
        }

        .hero-card h1 {
            font-size: 1.5rem;
            margin-bottom: 10px;
            color: var(--text-dark);
        }

        .hero-card p {
            font-size: 0.95rem;
            color: var(--text-gray);
            line-height: 1.5;
            max-width: 90%;
        }

        /* Dashboard Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
        }

        .stat-card {
            background: white;
            padding: 15px;
            border-radius: var(--radius-md);
            box-shadow: var(--shadow-sm);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .stat-header {
            font-size: 0.8rem;
            color: var(--text-gray);
            margin-bottom: 5px;
            display: flex;
            justify-content: space-between;
        }

        .stat-value {
            font-size: 1.8rem;
            font-weight: 800;
            color: var(--text-dark);
        }

        .stat-trend {
            font-size: 0.75rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 4px;
            margin-top: 5px;
        }

        .trend-up { color: var(--green-trend); }
        .trend-neutral { color: var(--orange-trend); }

        .stat-card.blue { border-bottom: 4px solid #1877F2; }
        .stat-card.orange { border-bottom: 4px solid #F7B928; }
        .stat-card.green { border-bottom: 4px solid #31A24C; }

        /* Experience Feed */
        .section-title {
            font-size: 1rem;
            font-weight: 700;
            color: var(--text-dark);
            margin: 10px 0 5px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .section-title span {
            font-size: 0.75rem;
            background: #E4E6EB;
            padding: 4px 8px;
            border-radius: 10px;
            color: var(--text-gray);
        }

        .exp-card {
            background: white;
            border-radius: var(--radius-lg);
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: var(--shadow-sm);
            border: 1px solid transparent;
            transition: 0.2s;
        }

        .exp-card:hover {
            border-color: var(--primary);
            box-shadow: var(--shadow-md);
            transform: translateY(-2px);
        }

        .exp-header {
            display: flex;
            gap: 15px;
            margin-bottom: 12px;
        }

        .exp-icon {
            width: 45px;
            height: 45px;
            background: #E7F3FF;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary);
            flex-shrink: 0;
        }
        .exp-icon.un { background: #E2F6F8; color: #00A9CE; }

        .exp-meta h3 {
            font-size: 1rem;
            color: var(--text-dark);
            margin-bottom: 2px;
        }

        .exp-meta h4 {
            font-size: 0.9rem;
            color: var(--text-gray);
            font-weight: 500;
        }

        .exp-date {
            font-size: 0.75rem;
            color: var(--text-light);
        }

        .exp-body {
            padding-left: 60px;
        }

        .exp-body ul {
            list-style: none;
        }

        .exp-body li {
            position: relative;
            padding-left: 15px;
            margin-bottom: 6px;
            font-size: 0.85rem;
            color: #444;
        }

        .exp-body li::before {
            content: "•";
            color: var(--primary);
            font-weight: bold;
            position: absolute;
            left: 0;
        }

        /* --- RIGHT PANEL --- */
        .right-panel {
            display: flex;
            flex-direction: column;
            gap: 20px;
            overflow-y: auto;
        }

        .panel-card {
            background: white;
            border-radius: var(--radius-lg);
            padding: 20px;
            box-shadow: var(--shadow-sm);
        }

        .ad-preview-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-top: 10px;
        }

        .ad-thumb {
            aspect-ratio: 1/1;
            background-color: #eee;
            border-radius: 8px;
            background-size: cover;
            background-position: center;
            position: relative;
            overflow: hidden;
            border: 1px solid #ddd;
        }

        .ad-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0,0,0,0.6);
            color: white;
            font-size: 0.6rem;
            padding: 4px;
            text-align: center;
        }

        .skills-list {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 10px;
        }

        .skill-tag {
            background: #F0F2F5;
            color: var(--text-dark);
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
        }

        .skill-tag.highlight {
            background: #E7F3FF;
            color: var(--primary);
        }

        .recent-results {
            list-style: none;
            margin-top: 10px;
        }

        .result-item {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 10px 0;
            border-bottom: 1px solid #eee;
        }

        .result-item:last-child { border-bottom: none; }

        .result-icon {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background: #F0F2F5;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
        }

        .result-text {
            font-size: 0.8rem;
            line-height: 1.2;
        }
        
        .result-text strong { display: block; color: var(--text-dark); }
        .result-text span { color: var(--text-light); font-size: 0.7rem; }

        /* Simulated Chart */
        .mini-chart {
            display: flex;
            align-items: flex-end;
            justify-content: space-between;
            height: 60px;
            margin-top: 15px;
            padding-bottom: 5px;
            border-bottom: 1px solid #eee;
        }

        .bar {
            width: 12%;
            background: #E4E6EB;
            border-radius: 4px 4px 0 0;
        }
        .bar.active { background: var(--primary); }

        /* Utility */
        .badge {
            display: inline-block;
            padding: 2px 6px;
            border-radius: 4px;
            font-size: 0.65rem;
            font-weight: 700;
            text-transform: uppercase;
        }
        .badge.meta { background: #E7F3FF; color: #1877F2; }
        .badge.ngo { background: #E6F6EC; color: #31A24C; }

    </style>
</head>
<body>

    <div class="cv-container">
        
        <aside class="sidebar">
            <div class="profile-header">
                <div class="avatar-ring">
                    <img src="![image](https://github.com/user-attachments/assets/d58b3d5a-0666-4d89-bf48-462cfd929c34)" alt="Javier Secaida" class="avatar-img">
                    <div class="status-dot"></div>
                </div>
                <h2 class="profile-name">Javier Secaida</h2>
                <p class="profile-role">Community Manager<br>Unidad Comunicacional</p>
            </div>

            <div class="contact-info">
                <div class="contact-row">
                    <svg viewBox="0 0 24 24"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/></svg>
                    <span>Guatemala</span>
                </div>
                <div class="contact-row">
                    <svg viewBox="0 0 24 24"><path d="M7.8 2h8.4C19.4 2 22 4.6 22 7.8v8.4a5.8 5.8 0 0 1-5.8 5.8H7.8C4.6 22 2 19.4 2 16.2V7.8A5.8 5.8 0 0 1 7.8 2m-.2 2A3.6 3.6 0 0 0 4 7.6v8.8C4 18.39 5.61 20 7.6 20h8.8a3.6 3.6 0 0 0 3.6-3.6V7.6C20 5.61 18.39 4 16.4 4H7.6m9.65 1.5a1.25 1.25 0 0 1 1.25 1.25A1.25 1.25 0 0 1 17.25 8 1.25 1.25 0 0 1 16 6.75a1.25 1.25 0 0 1 1.25-1.25M12 7a5 5 0 0 1 5 5 5 5 0 0 1-5 5 5 5 0 0 1-5-5 5 5 0 0 1 5-5m0 2a3 3 0 0 0-3 3 3 3 0 0 0 3 3 3 3 0 0 0 3-3 3 3 0 0 0-3-3z"/></svg>
                    <span>@xavi_nelson</span>
                </div>
            </div>

            <ul class="nav-menu">
                <li class="nav-item active">
                    <svg viewBox="0 0 24 24"><path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/></svg>
                    Inicio / Resumen
                </li>
                <li class="nav-item">
                    <svg viewBox="0 0 24 24"><path d="M20 6h-4V4c0-1.11-.89-2-2-2h-4c-1.11 0-2 .89-2 2v2H4c-1.11 0-1.99.89-1.99 2L2 19c0 1.11.89 2 2 2h16c1.11 0 2-.89 2-2V8c0-1.11-.89-2-2-2zm-6 0h-4V4h4v2z"/></svg>
                    Experiencia
                </li>
                <li class="nav-item">
                    <svg viewBox="0 0 24 24"><path d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"/></svg>
                    Habilidades
                </li>
                <li class="nav-item">
                    <svg viewBox="0 0 24 24"><path d="M19 3H5c-1.11 0-2 .9-2 2v14c0 1.1.89 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-2 10h-4v4h-2v-4H7v-2h4V7h2v4h4v2z"/></svg>
                    Referencias
                </li>
            </ul>

            <div class="sidebar-footer">
                <button class="btn-ref">Solivitar referencias</button>
            </div>
        </aside>

        <main class="main-content">
            <div class="search-bar-sim">
                <svg viewBox="0 0 24 24" style="width:20px; height:20px; fill: #65676B; margin-right:10px;"><path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3 9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/></svg>
                Buscar en experiencia, logros y campañas...
            </div>

            <div class="hero-card">
                <h1>Hola 👋 Soy Javier</h1>
                <p><strong>Community Manager</strong> enfocado en gestión de redes, diseño gráfico y pautas publicitarias con impacto social. Lidero estrategias digitales para ONGs y proyectos de cooperación internacional.</p>
            </div>

            <div class="section-title">Estadísticas Generales <span>Última experiencia</span></div>
            <div class="stats-grid">
                <div class="stat-card green">
                    <div class="stat-header">Interacciones <span>↗</span></div>
                    <div class="stat-value">33%</div>
                    <div class="stat-trend trend-up">
                        <svg viewBox="0 0 24 24" style="width:14px;fill:currentColor;"><path d="M7 14l5-5 5 5z"/></svg>
                        Aumento Orgánico
                    </div>
                </div>
                <div class="stat-card orange">
                    <div class="stat-header">Tráfico Web <span>↗</span></div>
                    <div class="stat-value">40%</div>
                    <div class="stat-trend trend-neutral">
                        <svg viewBox="0 0 24 24" style="width:14px;fill:currentColor;"><path d="M7 14l5-5 5 5z"/></svg>
                        Conversión Ads
                    </div>
                </div>
                <div class="stat-card blue">
                    <div class="stat-header">Campañas <span>★</span></div>
                    <div class="stat-value">Active</div>
                    <div class="stat-trend" style="color:#1877F2">
                        Meta Ads Expert
                    </div>
                </div>
            </div>

            <div class="section-title">Experiencia Profesional <span>Cronología</span></div>

            <div class="exp-card">
                <div class="exp-header">
                    <div class="exp-icon">
                        <svg viewBox="0 0 24 24" style="width:24px;fill:currentColor;"><path d="M12 7V3H2v18h20V7H12zM6 19H4v-2h2v2zm0-4H4v-2h2v2zm0-4H4V9h2v2zm0-4H4V5h2v2zm4 12H8v-2h2v2zm0-4H8v-2h2v2zm0-4H8V9h2v2zm0-4H8V5h2v2zm10 12h-8v-2h2v-2h-2v-2h2v-2h-2V9h8v10zm-2-8h-2v2h2v-2zm0 4h-2v2h2v-2z"/></svg>
                    </div>
                    <div class="exp-meta">
                        <h3>Coordinador de Unidad Comunicacional <span class="badge ngo">Crear ONG</span></h3>
                        <h4>Community Manager & Estratega</h4>
                        <span class="exp-date">Mayo 2025 - Diciembre 2025</span>
                    </div>
                </div>
                <div class="exp-body">
                    <ul>
                        <li>Gestión estratégica de redes sociales institucionales y planificación de contenido.</li>
                        <li>Creación y optimización de pautas publicitarias en <strong>Meta Ads</strong>.</li>
                        <li>Diseño gráfico de campañas visuales y análisis de rendimiento (KPIs).</li>
                        <li>Trabajo directo con organizaciones aliadas y cooperación internacional.</li>
                    </ul>
                </div>
            </div>

            <div class="exp-card">
                <div class="exp-header">
                    <div class="exp-icon un">
                        <svg viewBox="0 0 24 24" style="width:24px;fill:currentColor;"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/></svg>
                    </div>
                    <div class="exp-meta">
                        <h3>Proyecto Ciberciudadanos - Naciones Unidas</h3>
                        <h4>Apoyo Comunicacional & Gestión Digital</h4>
                        <span class="exp-date">Iniciativa Vinculada a ONU</span>
                    </div>
                </div>
                <div class="exp-body">
                    <ul>
                        <li>Creación de contenido para prevención de ciberviolencias.</li>
                        <li>Gestión de comunidades digitales para juventudes (entornos seguros).</li>
                        <li>Apoyo en estrategias de difusión y alcance orgánico.</li>
                    </ul>
                </div>
            </div>

             <div class="exp-card" style="opacity: 0.9;">
                <div class="exp-header">
                    <div class="exp-icon" style="background: #f0f0f0; color: #666;">
                        <svg viewBox="0 0 24 24" style="width:24px;fill:currentColor;"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm-5 14H9v-2h6v2zm-3-7c-1.66 0-3-1.34-3-3s1.34-3 3-3 3 1.34 3 3-1.34 3-3 3z"/></svg>
                    </div>
                    <div class="exp-meta">
                        <h3>Asesor de Ventas y Atención</h3>
                        <h4>iShop Guatemala</h4>
                        <span class="exp-date">Nov 2023 - Sept 2024</span>
                    </div>
                </div>
            </div>

        </main>

        <aside class="right-panel">
            
            <div class="panel-card">
                <div class="section-title" style="margin-top:0;">Top Pautas <span class="badge meta">Ads</span></div>
                <p style="font-size:0.75rem; color:#666; margin-bottom:10px;">Ejemplos de campañas gestionadas:</p>
                <div class="ad-preview-grid">
                    <a href="https://www.instagram.com/p/DNOL5y2Tmkl/" target="_blank" style="text-decoration:none;">
                        <div class="ad-thumb" style="background-image: url('<img width="1306" height="1640" alt="image" src="https://github.com/user-attachments/assets/fa79e0ef-d3e9-4ca7-a7fb-b94a4ac72afb" />
');">
                            <div class="ad-overlay">Ver Post ↗</div>
                        </div>
                    </a>
                    <a href="https://www.instagram.com/p/DLAwS2Dx6eQ/" target="_blank" style="text-decoration:none;">
                        <div class="ad-thumb" style="background-image: url('<img width="1306" height="1640" alt="image" src="https://github.com/user-attachments/assets/fa2fcf69-8a89-49ce-bee5-4fe5fc03f7aa" />
');">
                            <div class="ad-overlay">Ver Post ↗</div>
                        </div>
                    </a>
                </div>
            </div>

            <div class="panel-card">
                <div class="section-title" style="margin-top:0;">Habilidades</div>
                <div class="skills-list">
                    <span class="skill-tag highlight">Community Management</span>
                    <span class="skill-tag highlight">Meta Ads</span>
                    <span class="skill-tag">Diseño Gráfico</span>
                    <span class="skill-tag">Copywriting</span>
                    <span class="skill-tag">Comunicación Social</span>
                    <span class="skill-tag">KPI Analysis</span>
                    <span class="skill-tag">Juventudes</span>
                </div>
            </div>

            <div class="panel-card">
                <div class="section-title" style="margin-top:0;">Formación</div>
                <ul class="recent-results">
                    <li class="result-item">
                        <div class="result-icon">🎓</div>
                        <div class="result-text">
                            <strong>Ingeniería en Sistemas</strong>
                            <span>Univ. Mariano Gálvez (2024 - Actual)</span>
                        </div>
                    </li>
                    <li class="result-item">
                        <div class="result-icon">🏫</div>
                        <div class="result-text">
                            <strong>Bachiller en CCyL</strong>
                            <span>Orientación Computación (2022-2023)</span>
                        </div>
                    </li>
                </ul>
            </div>

            <div class="panel-card">
                <div class="section-title" style="margin-top:0;">Actividad Semanal</div>
                <div class="mini-chart">
                    <div class="bar" style="height: 40%"></div>
                    <div class="bar" style="height: 60%"></div>
                    <div class="bar" style="height: 30%"></div>
                    <div class="bar active" style="height: 80%"></div>
                    <div class="bar active" style="height: 95%"></div>
                    <div class="bar" style="height: 50%"></div>
                    <div class="bar" style="height: 70%"></div>
                </div>
                <p style="font-size:0.7rem; color:#999; text-align:center; margin-top:5px;">Publicaciones vs Interacciones</p>
            </div>

        </aside>
    </div>

</body>
</html>
