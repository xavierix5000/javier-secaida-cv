<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CV Javier Secaida - Community Manager</title>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <style>
        :root {
            --primary: #0084FF;
            --primary-light: #E7F3FF;
            --bg-gradient: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            --glass: rgba(255, 255, 255, 0.85);
            --text-dark: #1A1A1A;
            --text-gray: #65676B;
            --shadow: 0 8px 32px rgba(31, 38, 135, 0.1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background: var(--bg-gradient);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        /* Formato Tamaño Carta Vertical */
        .cv-page {
            width: 8.5in;
            height: 11in;
            background: var(--glass);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.5);
            border-radius: 24px;
            display: grid;
            grid-template-columns: 260px 1fr;
            box-shadow: var(--shadow);
            overflow: hidden;
            position: relative;
        }

        /* Botón de descarga flotante (no sale en el PDF) */
        .no-print-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            padding: 12px 24px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50px;
            font-weight: 700;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0,132,255,0.4);
            z-index: 100;
        }

        /* Barra Lateral */
        .sidebar {
            background: rgba(255, 255, 255, 0.4);
            padding: 40px 25px;
            border-right: 1px solid rgba(255, 255, 255, 0.3);
            display: flex;
            flex-direction: column;
            gap: 30px;
        }

        .profile-photo {
            width: 150px;
            height: 150px;
            margin: 0 auto;
            border-radius: 50%;
            border: 5px solid white;
            box-shadow: var(--shadow);
            object-fit: cover;
            background: white;
        }

        .contact-info h3 { font-size: 0.9rem; color: var(--primary); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 15px; }
        .contact-item { font-size: 0.85rem; margin-bottom: 10px; color: var(--text-dark); display: flex; align-items: center; gap: 8px; }

        .skills-section h3 { font-size: 0.9rem; color: var(--primary); text-transform: uppercase; margin-bottom: 15px; }
        .skill-badge {
            display: inline-block;
            padding: 6px 12px;
            background: white;
            border-radius: 8px;
            font-size: 0.75rem;
            font-weight: 600;
            margin: 0 5px 8px 0;
            border: 1px solid rgba(0,0,0,0.05);
        }

        /* Contenido Principal */
        .main-content {
            padding: 40px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        .header-intro h1 { font-size: 2.2rem; font-weight: 800; color: var(--text-dark); margin-bottom: 10px; }
        .header-intro p { font-size: 0.95rem; line-height: 1.6; color: var(--text-gray); }

        .section-header {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.1rem;
            font-weight: 800;
            color: var(--text-dark);
            margin-bottom: 15px;
        }
        .section-header span { width: 40px; height: 3px; background: var(--primary); border-radius: 2px; }

        .experience-card {
            background: white;
            padding: 20px;
            border-radius: 16px;
            margin-bottom: 15px;
            border: 1px solid rgba(0,0,0,0.03);
            transition: 0.3s;
        }
        .exp-meta { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 8px; }
        .exp-title { font-weight: 700; color: var(--primary); font-size: 1.05rem; }
        .exp-date { font-size: 0.8rem; font-weight: 600; color: var(--text-gray); }
        .exp-desc { font-size: 0.88rem; color: var(--text-gray); line-height: 1.5; }

        /* Métrica de Impacto (Sustituye a las barras) */
        .impact-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; }
        .impact-card {
            background: linear-gradient(135deg, #ffffff 0%, #f8fbff 100%);
            padding: 15px;
            border-radius: 16px;
            text-align: center;
            border: 1px solid var(--primary-light);
        }
        .impact-num { font-size: 1.4rem; font-weight: 800; color: var(--primary); display: block; }
        .impact-label { font-size: 0.7rem; font-weight: 700; text-transform: uppercase; color: var(--text-gray); }

        /* Instagram Posts Previews */
        .insta-previews { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .insta-card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid #eee;
            text-decoration: none;
        }
        .insta-img { width: 100%; height: 120px; background-size: cover; background-position: center; }
        .insta-info { padding: 10px; font-size: 0.75rem; color: var(--text-dark); font-weight: 600; }

        @media print {
            .no-print-btn { display: none; }
            body { background: white; padding: 0; }
            .cv-page { border: none; box-shadow: none; border-radius: 0; }
        }
    </style>
</head>
<body>

    <button class="no-print-btn" onclick="exportPDF()">Descargar CV en PDF</button>

    <div class="cv-page" id="cv-content">
        <aside class="sidebar">
            <img src="https://drive.google.com/uc?export=view&id=1kPH-1mXFxycWVHm6fQKee65mzLgVKrtk" alt="Javier Secaida" class="profile-photo">
            
            <div class="contact-info">
                <h3>Contacto</h3>
                <div class="contact-item">📧 javisecaida17@gmail.com</div>
                <div class="contact-item">📱 (502) 4536-6006</div>
                <div class="contact-item">📸 @xavi_nelson</div>
                <div class="contact-item">📍 Sacatepéquez, GT</div>
            </div>

            <div class="skills-section">
                <h3>Habilidades</h3>
                <div class="skill-badge">Meta Ads Expert</div>
                <div class="skill-badge">Community Management</div>
                <div class="skill-badge">Prevención Digital</div>
                <div class="skill-badge">Diseño Gráfico</div>
                <div class="skill-badge">Análisis de Datos</div>
                <div class="skill-badge">Gestión de Crisis</div>
            </div>

            <div class="skills-section">
                <h3>Formación</h3>
                <div style="font-size: 0.8rem; line-height: 1.4;">
                    [span_1](start_span)<p><strong>Ingeniería en Sistemas</strong><br>UMG (2024 - Actual)[span_1](end_span)</p>
                    [span_2](start_span)<p style="margin-top:10px;"><strong>Bachiller en CCyL</strong><br>IDEAS (2022-2023)[span_2](end_span)</p>
                </div>
            </div>
        </aside>

        <main class="main-content">
            <header class="header-intro">
                <h1>Hola 👋 Soy Javier</h1>
                <p>
                    [span_3](start_span)Soy una persona comprometida con la prevención de las ciberviolencias y con la creación de entornos digitales más seguros y positivos[span_3](end_span). [span_4](start_span)Como especialista en comunicación digital, mi enfoque es transformar espacios violentos en comunidades de paz, recreación y confianza[span_4](end_span).
                </p>
            </header>

            <div class="impact-grid">
                <div class="impact-card">
                    <span class="impact-num">33%</span>
                    <span class="impact-label">Engagement Orgánico</span>
                </div>
                <div class="impact-card">
                    <span class="impact-num">+40%</span>
                    <span class="impact-label">Alcance Mensual</span>
                </div>
                <div class="impact-card">
                    <span class="impact-num">Safe</span>
                    <span class="impact-label">Moderación Comunitaria</span>
                </div>
            </div>

            <section>
                <div class="section-header"><span></span> Experiencia Destacada</div>
                
                <div class="experience-card" style="border-left: 4px solid var(--primary);">
                    <div class="exp-meta">
                        <span class="exp-title">Coordinador Unidad Comunicacional</span>
                        <span class="exp-date">2025 - Actual</span>
                    </div>
                    [span_5](start_span)<p style="font-weight: 700; font-size: 0.85rem; margin-bottom: 5px;">CREAR ONG - Proyecto Vidas Dignas[span_5](end_span)</p>
                    <p class="exp-desc">
                        Lidero estrategias integrales para fortalecer la participación juvenil y la construcción de ambientes digitales dignos. [span_6](start_span)Responsable de la identidad visual y el posicionamiento de campañas sociales de alto impacto[span_6](end_span).
                    </p>
                </div>

                <div class="experience-card">
                    <div class="exp-meta">
                        <span class="exp-title">Apoyo Comunicacional</span>
                        <span class="exp-date">ONU - UNFPA</span>
                    </div>
                    [span_7](start_span)<p style="font-weight: 700; font-size: 0.85rem; margin-bottom: 5px;">Ciber Ciudadanos Jóvenes Construyendo Paz[span_7](end_span)</p>
                    <p class="exp-desc">
                        [span_8](start_span)Colaboración técnica en la transformación de narrativas digitales y gestión de plataformas para la prevención de violencia en línea en entornos juveniles[span_8](end_span).
                    </p>
                </div>

                <div class="experience-card">
                    <div class="exp-meta">
                        <span class="exp-title">Asesor de Ventas Especializado</span>
                        <span class="exp-date">2023 - 2024</span>
                    </div>
                    [span_9](start_span)<p style="font-weight: 700; font-size: 0.85rem; margin-bottom: 5px;">iShop Guatemala[span_9](end_span)</p>
                    [span_10](start_span)<p class="exp-desc">Optimización de experiencia de usuario y cumplimiento de objetivos comerciales mediante el conocimiento técnico de ecosistemas digitales[span_10](end_span).</p>
                </div>
            </section>

            <section>
                <div class="section-header"><span></span> Top Pautas Meta Ads</div>
                <div class="insta-previews">
                    <a href="https://www.instagram.com/p/DNOL5y2Tmkl/" target="_blank" class="insta-card">
                        <div class="insta-img" style="background-image: url('https://images.unsplash.com/photo-1611162617213-7d7a39e9b1d7?auto=format&fit=crop&w=400&q=80');"></div>
                        <div class="insta-info">Campaña Prevención Social ↗</div>
                    </a>
                    <a href="https://www.instagram.com/p/DLAwS2Dx6eQ/" target="_blank" class="insta-card">
                        <div class="insta-img" style="background-image: url('https://images.unsplash.com/photo-1551818255-e6e10975bc17?auto=format&fit=crop&w=400&q=80');"></div>
                        <div class="insta-info">Estrategia Participación Juvenil ↗</div>
                    </a>
                </div>
            </section>
        </main>
    </div>

    <script>
        function exportPDF() {
            const element = document.getElementById('cv-content');
            const opt = {
                margin: 0,
                filename: 'CV_Javier_Secaida_2026.pdf',
                image: { type: 'jpeg', quality: 0.98 },
                html2canvas: { scale: 3, useCORS: true },
                jsPDF: { unit: 'in', format: 'letter', orientation: 'portrait' }
            };
            html2pdf().set(opt).from(element).save();
        }
    </script>
</body>
</html>
