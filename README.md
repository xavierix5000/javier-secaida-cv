<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Javier Secaida - Portfolio Dashboard</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <style>
        :root {
            --meta-blue: #0668E1;
            --meta-bg: #F0F2F5;
            --glass: rgba(255, 255, 255, 0.9);
            --text-main: #1C1E21;
            --text-secondary: #65676B;
            --sidebar-width: 280px;
            --radius: 12px;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--meta-bg);
            color: var(--text-main);
            display: flex;
            justify-content: center;
            padding: 20px;
        }

        /* Contenedor Principal Estilo Dashboard */
        #cv-container {
            width: 1100px;
            background: white;
            display: grid;
            grid-template-columns: var(--sidebar-width) 1fr 300px;
            gap: 0;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 12px 40px rgba(0,0,0,0.12);
            min-height: 850px;
        }

        /* --- SIDEBAR IZQUIERDO --- */
        .sidebar {
            background: white;
            border-right: 1px solid #ddd;
            padding: 30px 20px;
            display: flex;
            flex-direction: column;
        }

        .profile-section { text-align: center; margin-bottom: 30px; }
        
        .profile-img-container {
            width: 120px;
            height: 120px;
            margin: 0 auto 15px;
            border-radius: 50%;
            border: 4px solid var(--meta-blue);
            padding: 3px;
            overflow: hidden;
        }

        .profile-img-container img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
        }

        .profile-section h2 { font-size: 1.2rem; font-weight: 800; }
        .profile-section p { font-size: 0.85rem; color: var(--text-secondary); }

        .nav-menu { list-style: none; margin-top: 20px; }
        .nav-menu li {
            padding: 12px 15px;
            border-radius: var(--radius);
            margin-bottom: 5px;
            font-size: 0.9rem;
            color: var(--text-secondary);
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 12px;
            cursor: pointer;
        }
        .nav-menu li.active { background: #E7F3FF; color: var(--meta-blue); }

        .contact-box {
            margin-top: auto;
            background: var(--meta-bg);
            padding: 15px;
            border-radius: var(--radius);
            font-size: 0.8rem;
        }

        /* --- CONTENIDO CENTRAL --- */
        .main-content {
            padding: 30px;
            background: #F9FAFB;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .welcome-card {
            background: linear-gradient(135deg, #0668E1, #00A1FF);
            color: white;
            padding: 25px;
            border-radius: 15px;
            position: relative;
        }

        .welcome-card h1 { font-size: 1.5rem; margin-bottom: 10px; }
        
        .download-btn {
            position: absolute;
            top: 25px;
            right: 25px;
            background: white;
            color: var(--meta-blue);
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 700;
            font-size: 0.8rem;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            transition: 0.2s;
        }
        .download-btn:hover { transform: translateY(-2px); background: #f0f0f0; }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
        }

        .stat-card {
            background: white;
            padding: 15px;
            border-radius: 12px;
            border: 1px solid #eee;
            text-align: center;
        }
        .stat-val { font-size: 1.5rem; font-weight: 800; display: block; }
        .stat-label { font-size: 0.75rem; color: var(--text-secondary); text-transform: uppercase; }

        .exp-section { background: white; padding: 20px; border-radius: 15px; border: 1px solid #eee; }
        .section-title { font-size: 0.9rem; font-weight: 800; margin-bottom: 15px; color: var(--text-secondary); border-bottom: 2px solid var(--meta-bg); padding-bottom: 5px; }

        .job-card { margin-bottom: 20px; padding-left: 15px; border-left: 3px solid #E7F3FF; }
        .job-card h3 { font-size: 1rem; color: var(--meta-blue); }
        .job-card span { font-size: 0.75rem; color: var(--text-secondary); font-weight: 600; }
        .job-card p { font-size: 0.85rem; margin-top: 5px; line-height: 1.4; }

        /* --- PANEL DERECHO --- */
        .right-panel {
            padding: 30px 20px;
            background: white;
            border-left: 1px solid #ddd;
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        .pautas-grid {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .pauta-item {
            display: flex;
            align-items: center;
            gap: 10px;
            text-decoration: none;
            color: var(--text-main);
            padding: 10px;
            border: 1px solid #eee;
            border-radius: 10px;
            transition: 0.2s;
        }
        .pauta-item:hover { background: #f8f9fa; border-color: var(--meta-blue); }
        
        .pauta-img { width: 50px; height: 50px; background: #ddd; border-radius: 8px; flex-shrink: 0; }

        .skill-tag {
            display: inline-block;
            background: var(--meta-bg);
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
            margin: 0 4px 8px 0;
            color: var(--text-secondary);
        }

        .chart-sim {
            height: 80px;
            display: flex;
            align-items: flex-end;
            gap: 6px;
            margin-top: 15px;
        }
        .bar { flex: 1; background: #E4E6EB; border-radius: 4px; }
        .bar.blue { background: var(--meta-blue); }

    </style>
</head>
<body>

    <div id="cv-container">
        <aside class="sidebar">
            <div class="profile-section">
                <div class="profile-img-container">
                    <img src="https://drive.google.com/uc?export=view&id=1kPH-1mXFxycWVHm6fQKee65mzLgVKrtk" alt="Javier Secaida">
                </div>
                <h2>Javier Secaida</h2>
                <p>Community Manager</p>
            </div>

            <ul class="nav-menu">
                <li class="active">🏠 Inicio / Feed</li>
                <li>📊 Estadísticas</li>
                <li>📂 Experiencia</li>
                <li>💡 Habilidades</li>
                <li>🎓 Formación</li>
            </ul>

            <div class="contact-box">
                <p><strong>Email:</strong> javisecaida17@gmail.com</p>
                <p><strong>WhatsApp:</strong> +502 4536-6006</p>
                <p><strong>Instagram:</strong> @xavi_nelson</p>
                <p style="margin-top: 10px;">📍 Escuintla, Guatemala</p>
            </div>
        </aside>

        <main class="main-content">
            <div class="welcome-card">
                <h1>Hola 👋 Soy Javier</h1>
                <p>Gestiono comunidades digitales y pautas publicitarias con enfoque social y preventivo.</p>
                <button class="download-btn" onclick="downloadPDF()">Descargar PDF</button>
            </div>

            <div class="stats-grid">
                <div class="stat-card">
                    <span class="stat-val" style="color: #31A24C;">+33%</span>
                    <span class="stat-label">Interacciones</span>
                </div>
                <div class="stat-card">
                    <span class="stat-val" style="color: #F7B928;">+40%</span>
                    <span class="stat-label">Tráfico Web</span>
                </div>
                <div class="stat-card">
                    <span class="stat-val" style="color: var(--meta-blue);">100%</span>
                    <span class="stat-label">Compromiso</span>
                </div>
            </div>

            <div class="exp-section">
                <div class="section-title">EXPERIENCIA PROFESIONAL</div>
                
                <div class="job-card">
                    <h3>Consultor en Comunicación Digital</h3>
                    <span>Colectiva Enfócate | Sept 2025 - Actualidad</span>
                    <p>Desarrollo de estrategias de contenido y manejo de comunidades para impacto social.</p>
                </div>

                <div class="job-card">
                    <h3>Coordinador Unidad Comunicar</h3>
                    <span>CREAR ONG | Mayo 2025 - Dic 2025</span>
                    <p>Liderazgo de estrategias para fortalecer la participación juvenil y entornos digitales dignos.</p>
                </div>

                <div class="job-card">
                    <h3>Proyecto Ciberciudadanos</h3>
                    <span>Naciones Unidas (UNFPA) | Participación</span>
                    <p>Transformación de espacios digitales violentos en comunidades de paz y confianza.</p>
                </div>

                <div class="job-card">
                    <h3>Asesor de Ventas</h3>
                    <span>iShop | Nov 2023 - Sept 2024</span>
                    <p>Atención al cliente especializada y cumplimiento de metas comerciales.</p>
                </div>
            </div>
        </main>

        <aside class="right-panel">
            <div>
                <div class="section-title">TOP PAUTAS (META ADS)</div>
                <div class="pautas-grid">
                    <a href="https://www.instagram.com/p/DNOL5y2Tmkl/" target="_blank" class="pauta-item">
                        <div class="pauta-img" style="background: url('https://img.icons8.com/color/96/instagram-new.png') center/cover;"></div>
                        <div style="font-size: 0.75rem;"><strong>Campaña Prevención</strong><br>Ver en Instagram ↗</div>
                    </a>
                    <a href="https://www.instagram.com/p/DLAwS2Dx6eQ/" target="_blank" class="pauta-item">
                        <div class="pauta-img" style="background: url('https://img.icons8.com/color/96/instagram-new.png') center/cover;"></div>
                        <div style="font-size: 0.75rem;"><strong>Participación Juvenil</strong><br>Ver en Instagram ↗</div>
                    </a>
                </div>
            </div>

            <div>
                <div class="section-title">HABILIDADES</div>
                <div class="skill-tag">Meta Ads Expert</div>
                <div class="skill-tag">Community Management</div>
                <div class="skill-tag">Diseño Gráfico</div>
                <div class="skill-tag">Prevención Digital</div>
                <div class="skill-tag">KPI Analysis</div>
                <div class="skill-tag">Empatía</div>
            </div>

            <div>
                <div class="section-title">ACTIVIDAD SEMANAL</div>
                <div class="chart-sim">
                    <div class="bar" style="height: 30%;"></div>
                    <div class="bar blue" style="height: 60%;"></div>
                    <div class="bar" style="height: 45%;"></div>
                    <div class="bar blue" style="height: 85%;"></div>
                    <div class="bar" style="height: 50%;"></div>
                </div>
                <p style="font-size: 0.65rem; color: #999; margin-top: 10px; text-align: center;">Rendimiento de publicaciones vs pautas</p>
            </div>

            <div style="margin-top: auto;">
                <div class="section-title">EDUCACIÓN</div>
                <p style="font-size: 0.75rem;"><strong>Ingeniería en Sistemas</strong><br>UMG (En curso)</p>
            </div>
        </aside>
    </div>

    <script>
        function downloadPDF() {
            const element = document.getElementById('cv-container');
            const opt = {
                margin: 0,
                filename: 'CV_Javier_Secaida_2026.pdf',
                image: { type: 'jpeg', quality: 0.98 },
                html2canvas: { scale: 2, useCORS: true },
                jsPDF: { unit: 'in', format: 'a4', orientation: 'landscape' }
            };
            html2pdf().set(opt).from(element).save();
        }
    </script>
</body>
</html>
