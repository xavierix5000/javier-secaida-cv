<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CV Javier Secaida - Dashboard Profesional</title>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <style>
        :root {
            --meta-blue: #0084FF;
            --meta-bg: #F0F2F5;
            --text-dark: #1C1E21;
            --text-gray: #65676B;
            --glass: rgba(255, 255, 255, 0.9);
            --shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #E9EBEE;
            display: flex;
            justify-content: center;
            padding: 40px 0;
            color: var(--text-dark);
        }

        /* Contenedor Tamaño Carta Vertical */
        #cv-carta {
            width: 8.5in;
            height: 11in;
            background: white;
            box-shadow: 0 0 40px rgba(0,0,0,0.15);
            display: grid;
            grid-template-columns: 260px 1fr;
            overflow: hidden;
            position: relative;
        }

        /* BARRA LATERAL (SIDEBAR) */
        .sidebar {
            background: #ffffff;
            border-right: 1px solid #ddd;
            padding: 40px 25px;
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        .profile-pic {
            width: 160px;
            height: 160px;
            border-radius: 50%;
            border: 4px solid var(--meta-blue);
            margin: 0 auto;
            object-fit: cover;
            box-shadow: var(--shadow);
        }

        .sidebar-section h3 {
            font-size: 0.85rem;
            color: var(--meta-blue);
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 12px;
            border-bottom: 1px solid #eee;
            padding-bottom: 5px;
        }

        .contact-item { font-size: 0.8rem; margin-bottom: 8px; color: var(--text-gray); display: flex; align-items: center; gap: 8px; }
        
        .skill-tag {
            display: inline-block;
            background: #f0f7ff;
            color: var(--meta-blue);
            padding: 5px 10px;
            border-radius: 6px;
            font-size: 0.75rem;
            font-weight: 600;
            margin: 0 4px 6px 0;
        }

        /* CONTENIDO PRINCIPAL */
        .main-content {
            padding: 40px;
            background: #F9FAFB;
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        .intro-header {
            background: linear-gradient(135deg, #0084FF, #0056b3);
            color: white;
            padding: 30px;
            border-radius: 16px;
            position: relative;
        }

        .intro-header h1 { font-size: 1.8rem; margin-bottom: 10px; font-weight: 800; }
        .intro-header p { font-size: 0.88rem; line-height: 1.6; opacity: 0.95; }

        /* Impact Metrics (Reemplazan las barras sin sentido) */
        .impact-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; }
        .impact-card {
            background: white;
            padding: 15px;
            border-radius: 12px;
            border: 1px solid #eee;
            text-align: center;
        }
        .impact-val { font-size: 1.3rem; font-weight: 800; color: var(--meta-blue); display: block; }
        .impact-label { font-size: 0.7rem; color: var(--text-gray); font-weight: 700; text-transform: uppercase; }

        .section-title {
            font-size: 1.1rem;
            font-weight: 800;
            color: var(--text-dark);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .section-title::after { content: ""; height: 2px; background: #eee; flex-grow: 1; }

        .exp-item {
            background: white;
            padding: 18px;
            border-radius: 12px;
            border-left: 4px solid var(--meta-blue);
            margin-bottom: 15px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.02);
        }
        .exp-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 5px; }
        .exp-company { font-weight: 800; color: var(--meta-blue); font-size: 0.95rem; }
        .exp-date { font-size: 0.75rem; color: var(--text-gray); font-weight: 600; }
        .exp-role { font-weight: 700; font-size: 0.88rem; display: block; margin-bottom: 8px; }
        .exp-desc { font-size: 0.82rem; line-height: 1.5; color: var(--text-gray); }

        /* Instagram Post Previews */
        .portfolio-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .insta-card {
            background: white;
            border-radius: 10px;
            border: 1px solid #ddd;
            overflow: hidden;
            text-decoration: none;
            color: inherit;
        }
        .insta-img {
            width: 100%;
            height: 100px;
            background-color: #f0f0f0;
            background-size: cover;
            background-position: center;
            border-bottom: 1px solid #eee;
        }
        .insta-caption { padding: 8px; font-size: 0.7rem; font-weight: 600; }

        /* Botón de Descarga */
        .btn-download {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: #1C1E21;
            color: white;
            border: none;
            padding: 15px 25px;
            border-radius: 50px;
            font-weight: 700;
            cursor: pointer;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            z-index: 100;
        }

        @media print {
            .btn-download { display: none; }
            body { padding: 0; background: white; }
            #cv-carta { box-shadow: none; }
        }
    </style>
</head>
<body>

    <button class="btn-download" onclick="generarPDF()">Descargar CV en PDF</button>

    <div id="cv-carta">
        <aside class="sidebar">
            <img src="https://github.com/user-attachments/assets/43111609-3642-403b-8976-bbaf2d53aab0" alt="Javier Secaida" class="profile-pic">
            
            <div class="sidebar-section">
                <h3>Contacto</h3>
                <div class="contact-item">📧 javisecaida17@gmail.com</div>
                <div class="contact-item">📱 (502) 4536-6006</div>
                <div class="contact-item">📍 Sacatepéquez, GT</div>
                <div class="contact-item">📸 @xavi_nelson</div>
            </div>

            <div class="sidebar-section">
                <h3>Habilidades</h3>
                <div class="skill-tag">Meta Ads</div>
                <div class="skill-tag">Gestión de Crisis</div>
                <div class="skill-tag">Diseño Gráfico</div>
                <div class="skill-tag">Prevención Digital</div>
                <div class="skill-tag">Copywriting</div>
                <div class="skill-tag">KPI Analysis</div>
            </div>

            <div class="sidebar-section">
                <h3>Formación</h3>
                <div style="font-size: 0.75rem; line-height: 1.4;">
                    <p><strong>Ingeniería en Sistemas</strong><br>UMG (2024 - Actual)</p>
                    <p style="margin-top: 10px;"><strong>Bachiller en CCyL</strong><br>IDEAS Escuintla (2022-2023)</p>
                </div>
            </div>

            <div style="margin-top: auto; font-size: 0.65rem; color: #999;">
                Referencias disponibles a solicitud.
            </div>
        </aside>

        <main class="main-content">
            <header class="intro-header">
                <h1>Hola 👋 Soy Javier Secaida</h1>
                <p>
                    [span_1](start_span)Soy una persona comprometida con la prevención de las ciberviolencias y con la creación de entornos digitales más seguros y positivos. Con experiencia en la transformación de espacios digitales violentos en comunidades de paz, recreación y confianza.[span_1](end_span)
                </p>
            </header>

            <div class="impact-grid">
                <div class="impact-card">
                    <span class="impact-val">+33%</span>
                    <span class="impact-label">Interacciones</span>
                </div>
                <div class="impact-card" style="border-top: 3px solid #31A24C;">
                    <span class="impact-val">+40%</span>
                    <span class="impact-label">Alcance Web</span>
                </div>
                <div class="impact-card" style="border-top: 3px solid #f7b928;">
                    <span class="impact-val">Safe</span>
                    <span class="impact-label">Moderación</span>
                </div>
            </div>

            <section>
                <h2 class="section-title">Experiencia Profesional</h2>
                
                <div class="exp-item">
                    <div class="exp-header">
                        <span class="exp-company">CREAR ONG - Proyecto Vidas Dignas</span>
                        <span class="exp-date">Mayo 2025 - Dic. 2025</span>
                    </div>
                    <span class="exp-role">Coordinador de la Unidad Comunicacional</span>
                    <p class="exp-desc">
                        Liderazgo de estrategias integrales de comunicación para fortalecer la participación juvenil. [span_2](start_span)Gestión de identidad visual y campañas de impacto social.[span_2](end_span)
                    </p>
                </div>

                <div class="exp-item">
                    <div class="exp-header">
                        <span class="exp-company">Naciones Unidas (UNFPA)</span>
                        <span class="exp-date">Ciber Ciudadanos</span>
                    </div>
                    <span class="exp-role">Apoyo Comunicacional & Gestión Digital</span>
                    <p class="exp-desc">
                        [span_3](start_span)Desarrollo de contenido para la prevención de violencia digital y construcción de entornos seguros para juventudes.[span_3](end_span)
                    </p>
                </div>

                <div class="exp-item">
                    <div class="exp-header">
                        <span class="exp-company">iShop Guatemala</span>
                        <span class="exp-date">Nov. 2023 - Sept. 2024</span>
                    </div>
                    <span class="exp-role">Asesor de Ventas y Atención</span>
                    [span_4](start_span)<p class="exp-desc">Especialista en experiencia del cliente y asesoría técnica en tecnología de consumo.[span_4](end_span)</p>
                </div>
            </section>

            <section>
                <h2 class="section-title">Portafolio / Meta Ads</h2>
                <div class="portfolio-grid">
                    <a href="https://www.instagram.com/p/DNOL5y2Tmkl/" target="_blank" class="insta-card">
                        <div class="insta-img" style="background-image: url('https://images.unsplash.com/photo-1611162617213-7d7a39e9b1d7?auto=format&fit=crop&w=400&q=80');"></div>
                        <div class="insta-caption">Campaña Prevención Social ↗</div>
                    </a>
                    <a href="https://www.instagram.com/p/DLAwS2Dx6eQ/" target="_blank" class="insta-card">
                        <div class="insta-img" style="background-image: url('https://images.unsplash.com/photo-1551818255-e6e10975bc17?auto=format&fit=crop&w=400&q=80');"></div>
                        <div class="insta-caption">Gestión Participación Juvenil ↗</div>
                    </a>
                </div>
            </section>
        </main>
    </div>

    <script>
        function generarPDF() {
            const element = document.getElementById('cv-carta');
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
