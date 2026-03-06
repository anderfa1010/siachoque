# siachoque.github.io
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Proyecto Siachoque</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Source+Sans+3:wght@300;400;500;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --verde: #2d6a4f;
            --verde-claro: #40916c;
            --verde-suave: #74c69d;
            --crema: #fefae0;
            --tierra: #dda15e;
            --tierra-oscura: #bc6c25;
            --gris: #f8f9fa;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            font-family: 'Source Sans 3', sans-serif;
            background-color: #f5f0e8;
            min-height: 100vh;
        }

        /* ─── NAV ─── */
        #main-nav {
            background: linear-gradient(135deg, var(--verde) 0%, #1b4332 100%);
            position: sticky;
            top: 0;
            z-index: 999;
            box-shadow: 0 4px 20px rgba(0,0,0,0.25);
        }

        .nav-inner {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .nav-brand {
            font-family: 'Playfair Display', serif;
            font-size: 1.6rem;
            font-weight: 900;
            color: #fff;
            letter-spacing: -0.5px;
            padding: 1rem 0;
            display: flex;
            align-items: center;
            gap: 0.6rem;
        }

        .nav-brand span.leaf {
            font-size: 1.4rem;
        }

        .nav-tabs {
            display: flex;
            gap: 0;
        }

        .nav-tab {
            padding: 1.1rem 1.6rem;
            color: rgba(255,255,255,0.7);
            font-weight: 500;
            font-size: 0.95rem;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.25s ease;
            letter-spacing: 0.3px;
            background: none;
            border-top: none;
            border-left: none;
            border-right: none;
        }

        .nav-tab:hover {
            color: #fff;
            background: rgba(255,255,255,0.08);
        }

        .nav-tab.active {
            color: var(--tierra);
            border-bottom-color: var(--tierra);
            background: rgba(255,255,255,0.06);
        }

        /* ─── PAGE SECTIONS ─── */
        .page-section { display: none; }
        .page-section.active { display: block; }

        /* ─── INICIO ─── */
        .hero {
            background: linear-gradient(160deg, #1b4332 0%, var(--verde) 50%, #52b788 100%);
            min-height: 420px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            overflow: hidden;
            padding: 4rem 2rem;
        }

        .hero::before {
            content: '';
            position: absolute;
            inset: 0;
            background-image: radial-gradient(circle at 20% 50%, rgba(255,255,255,0.06) 0%, transparent 60%),
                              radial-gradient(circle at 80% 20%, rgba(116,198,157,0.2) 0%, transparent 50%);
        }

        .hero-content { position: relative; z-index: 1; max-width: 750px; }

        .hero-badge {
            display: inline-block;
            background: rgba(255,255,255,0.15);
            color: #d8f3dc;
            font-size: 0.8rem;
            font-weight: 600;
            letter-spacing: 2px;
            text-transform: uppercase;
            padding: 0.4rem 1.2rem;
            border-radius: 100px;
            border: 1px solid rgba(255,255,255,0.25);
            margin-bottom: 1.5rem;
        }

        .hero h1 {
            font-family: 'Playfair Display', serif;
            font-size: clamp(2.5rem, 6vw, 4rem);
            font-weight: 900;
            color: #fff;
            line-height: 1.1;
            margin-bottom: 1.2rem;
        }

        .hero h1 em {
            font-style: normal;
            color: var(--tierra);
        }

        .hero p {
            font-size: 1.15rem;
            color: rgba(255,255,255,0.85);
            line-height: 1.7;
            font-weight: 300;
            max-width: 580px;
            margin: 0 auto;
        }

        /* Info cards */
        .info-section {
            max-width: 1200px;
            margin: 0 auto;
            padding: 4rem 2rem;
        }

        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: 2rem;
            font-weight: 700;
            color: var(--verde);
            margin-bottom: 0.5rem;
        }

        .section-subtitle {
            color: #666;
            font-size: 1rem;
            margin-bottom: 2.5rem;
            font-weight: 300;
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
            gap: 1.5rem;
            margin-bottom: 3rem;
        }

        .info-card {
            background: #fff;
            border-radius: 16px;
            padding: 2rem;
            box-shadow: 0 2px 16px rgba(0,0,0,0.07);
            border-top: 4px solid var(--verde-suave);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .info-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 8px 30px rgba(0,0,0,0.12);
        }

        .info-card .icon {
            font-size: 2.2rem;
            margin-bottom: 1rem;
        }

        .info-card h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.2rem;
            color: var(--verde);
            margin-bottom: 0.6rem;
        }

        .info-card p {
            font-size: 0.93rem;
            color: #555;
            line-height: 1.65;
        }

        /* Gallery */
        .gallery-section {
            background: #fff;
            border-radius: 20px;
            padding: 2.5rem;
            box-shadow: 0 2px 16px rgba(0,0,0,0.07);
            margin-bottom: 3rem;
        }

        .gallery-section h2 {
            font-family: 'Playfair Display', serif;
            font-size: 1.5rem;
            color: var(--verde);
            margin-bottom: 0.3rem;
        }

        .gallery-section p.desc {
            color: #777;
            font-size: 0.9rem;
            margin-bottom: 1.5rem;
        }

        .upload-area {
            border: 2px dashed #b7e4c7;
            border-radius: 12px;
            padding: 2.5rem;
            text-align: center;
            cursor: pointer;
            background: #f0faf5;
            transition: all 0.2s;
            margin-bottom: 1.5rem;
        }

        .upload-area:hover, .upload-area.drag-over {
            border-color: var(--verde-claro);
            background: #d8f3dc;
        }

        .upload-area .upload-icon { font-size: 2.5rem; margin-bottom: 0.5rem; }

        .upload-area p {
            color: var(--verde);
            font-weight: 500;
            margin-bottom: 0.3rem;
        }

        .upload-area small { color: #888; font-size: 0.82rem; }

        #file-input { display: none; }

        .btn-upload {
            display: inline-block;
            margin-top: 1rem;
            padding: 0.6rem 1.8rem;
            background: var(--verde);
            color: #fff;
            border-radius: 8px;
            font-weight: 600;
            font-size: 0.9rem;
            cursor: pointer;
            border: none;
            transition: background 0.2s;
        }

        .btn-upload:hover { background: var(--verde-claro); }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            gap: 1rem;
        }

        .gallery-item {
            position: relative;
            border-radius: 10px;
            overflow: hidden;
            aspect-ratio: 1;
            background: #eee;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            animation: fadeIn 0.4s ease;
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
        }

        .gallery-item .delete-img {
            position: absolute;
            top: 6px;
            right: 6px;
            background: rgba(220,38,38,0.85);
            color: #fff;
            border: none;
            border-radius: 50%;
            width: 26px;
            height: 26px;
            font-size: 0.75rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.2s;
        }

        .gallery-item:hover .delete-img { opacity: 1; }

        .gallery-empty {
            text-align: center;
            color: #aaa;
            font-size: 0.9rem;
            padding: 1.5rem 0;
            display: none;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        /* ─── GERIATRÍA ─── */
        #page-geriatria {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        .geri-header {
            background: linear-gradient(135deg, #1b4332, var(--verde-claro));
            border-radius: 16px;
            padding: 2rem 2.5rem;
            margin-bottom: 2rem;
            color: #fff;
        }

        .geri-header h2 {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            font-weight: 700;
        }

        .geri-header p { opacity: 0.8; font-size: 0.95rem; margin-top: 0.3rem; }

        /* Cards & Charts */
        .card {
            background: #fff;
            border-radius: 12px;
            box-shadow: 0 2px 12px rgba(0,0,0,0.07);
            transition: all 0.25s ease;
        }

        .card:hover {
            box-shadow: 0 6px 24px rgba(0,0,0,0.12);
        }

        .chart-container { position: relative; height: 280px; width: 100%; }

        .btn-primary {
            background: var(--verde);
            color: white;
            font-weight: 600;
            padding: 0.55rem 1.2rem;
            border-radius: 8px;
            transition: background 0.2s;
            border: none;
            cursor: pointer;
            font-family: 'Source Sans 3', sans-serif;
            font-size: 0.9rem;
        }

        .btn-primary:hover { background: var(--verde-claro); }

        .btn-secondary {
            background: #6c757d;
            color: white;
            font-weight: 600;
            padding: 0.55rem 1.2rem;
            border-radius: 8px;
            transition: background 0.2s;
            border: none;
            cursor: pointer;
            font-family: 'Source Sans 3', sans-serif;
            font-size: 0.9rem;
        }

        .btn-secondary:hover { background: #5a6268; }

        .btn-danger {
            background: #dc3545;
            color: white;
            padding: 0.25rem 0.6rem;
            border-radius: 6px;
            font-size: 0.78rem;
            border: none;
            cursor: pointer;
            font-family: 'Source Sans 3', sans-serif;
        }

        .btn-danger:hover { background: #c82333; }

        .patient-list-item.active {
            background: #d8f3dc;
            border-left: 4px solid var(--verde);
        }

        .tab-button {
            padding: 0.45rem 1rem;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.88rem;
            transition: all 0.2s;
            border: none;
            font-family: 'Source Sans 3', sans-serif;
        }

        .tab-button.active { background: var(--verde); color: white; }
        .tab-button:not(.active) { background: #e9ecef; color: #495057; }

        .modal {
            display: none; position: fixed; z-index: 2000;
            left: 0; top: 0; width: 100%; height: 100%;
            overflow: auto; background: rgba(0,0,0,0.55);
            align-items: center; justify-content: center;
        }

        .modal-content {
            background: #fefefe; margin: auto;
            padding: 2rem; border: 1px solid #ddd;
            width: 92%; max-width: 800px; border-radius: 16px;
        }

        .close-button {
            color: #aaa; float: right; font-size: 28px;
            font-weight: bold; cursor: pointer; line-height: 1;
        }

        .close-button:hover { color: #333; }

        fieldset { border: 1px solid #dee2e6; border-radius: 8px; }
        legend { color: var(--verde); font-weight: 600; }

        .morisky-label {
            display: block; padding: 0.7rem; border: 2px solid #e2e8f0;
            border-radius: 8px; text-align: center; cursor: pointer;
            transition: all 0.2s; flex: 1; font-size: 0.9rem;
        }

        .morisky-label:hover { background: #f0faf5; border-color: var(--verde-suave); }

        .morisky-radio:checked + .morisky-label {
            background: var(--verde);
            border-color: var(--verde-claro);
            color: white;
            font-weight: 700;
        }

        /* ─── FOOTER ─── */
        footer {
            background: #1b4332;
            color: rgba(255,255,255,0.6);
            text-align: center;
            padding: 1.5rem;
            font-size: 0.85rem;
            margin-top: 4rem;
        }

        footer strong { color: var(--tierra); }

        /* Responsive nav */
        @media (max-width: 640px) {
            .nav-brand { font-size: 1.2rem; }
            .nav-tab { padding: 1rem 0.9rem; font-size: 0.82rem; }
            .hero h1 { font-size: 2rem; }
        }
    </style>
</head>
<body>

<!-- ══════════════════ NAVEGACIÓN ══════════════════ -->
<nav id="main-nav">
    <div class="nav-inner">
        <div class="nav-brand">
            <span class="leaf">🌿</span> Proyecto Siachoque
        </div>
        <div class="nav-tabs">
            <button class="nav-tab active" data-target="page-inicio">🏠 Inicio</button>
            <button class="nav-tab" data-target="page-geriatria">🩺 Seguimiento Geriátrico</button>
        </div>
    </div>
</nav>

<!-- ══════════════════ PÁGINA: INICIO ══════════════════ -->
<div id="page-inicio" class="page-section active">

    <div class="hero">
        <div class="hero-content">
            <div class="hero-badge">🌿 Boyacá, Colombia</div>
            <h1>Proyecto <em>Siachoque</em></h1>
            <p>Un programa comunitario de atención integral al adulto mayor, comprometido con el bienestar, la dignidad y la salud de nuestra comunidad.</p>
        </div>
    </div>

    <div class="info-section">

        <div style="text-align:center; margin-bottom:3rem;">
            <div class="section-title" style="display:inline-block;">¿Qué es el Proyecto Siachoque?</div>
            <p class="section-subtitle">Conoce nuestra misión, visión y los pilares que nos guían</p>
        </div>

        <div class="cards-grid">
            <div class="info-card">
                <div class="icon">🎯</div>
                <h3>Misión</h3>
                <p>Brindar atención médica integral y seguimiento continuo a los adultos mayores del municipio de Siachoque, fortaleciendo su calidad de vida mediante herramientas de valoración geriátrica y acompañamiento comunitario.</p>
            </div>
            <div class="info-card">
                <div class="icon">🌄</div>
                <h3>Visión</h3>
                <p>Ser un modelo de atención primaria en salud para comunidades rurales de Boyacá, donde cada adulto mayor recibe cuidado personalizado con dignidad y calidez humana.</p>
            </div>
            <div class="info-card">
                <div class="icon">🤝</div>
                <h3>Compromiso Comunitario</h3>
                <p>Trabajamos de la mano con las familias, líderes comunitarios y personal de salud del municipio para garantizar que ningún adulto mayor quede sin atención ni seguimiento.</p>
            </div>
            <div class="info-card" style="border-top-color: var(--tierra);">
                <div class="icon">📊</div>
                <h3>Herramientas de Valoración</h3>
                <p>Utilizamos escalas validadas internacionalmente: SPPB, Pfeiffer, Morisky-Green, Up and Go y Framingham para un seguimiento riguroso y científico del estado de salud.</p>
            </div>
            <div class="info-card" style="border-top-color: var(--tierra);">
                <div class="icon">👩‍⚕️</div>
                <h3>Equipo de Salud</h3>
                <p>Médicos, enfermeras y promotores de salud capacitados en geriatría trabajando juntos en visitas domiciliarias y consultas periódicas para cada paciente registrado.</p>
            </div>
            <div class="info-card" style="border-top-color: var(--tierra);">
                <div class="icon">📍</div>
                <h3>Ubicación</h3>
                <p>Municipio de Siachoque, Boyacá, Colombia. Atendemos veredas y el casco urbano, llegando a los adultos mayores donde viven con un enfoque de salud rural e intercultural.</p>
            </div>
        </div>

        <!-- Galería de imágenes -->
        <div class="gallery-section">
            <h2>📸 Galería del Proyecto</h2>
            <p class="desc">Carga imágenes del programa, actividades comunitarias, equipo de salud y más.</p>

            <div class="upload-area" id="upload-area">
                <div class="upload-icon">🖼️</div>
                <p>Arrastra y suelta imágenes aquí</p>
                <small>PNG, JPG, WEBP — máximo 10 MB por imagen</small>
                <br>
                <button class="btn-upload" onclick="document.getElementById('file-input').click()">Seleccionar imágenes</button>
            </div>
            <input type="file" id="file-input" multiple accept="image/*">

            <div id="gallery-empty" class="gallery-empty" style="display:block;">
                <p>🌿 Aún no hay imágenes cargadas. ¡Agrega fotos del proyecto!</p>
            </div>

            <div id="gallery-grid" class="gallery-grid"></div>
        </div>

    </div>
</div>

<!-- ══════════════════ PÁGINA: GERIATRÍA ══════════════════ -->
<div id="page-geriatria" class="page-section">
<div id="page-geriatria-inner">

    <div class="geri-header" style="margin-top:2rem; max-width:1200px; margin-left:auto; margin-right:auto; margin-top:2rem;">
        <h2>🩺 Plataforma de Seguimiento Geriátrico</h2>
        <p>Gestión y visualización de escalas de valoración integral del adulto mayor — Siachoque, Boyacá</p>
    </div>

    <div style="max-width:1200px; margin:0 auto; padding:0 2rem 2rem;">
        <div style="display:grid; grid-template-columns: 1fr 2fr; gap:2rem;" id="geri-layout">

            <!-- Sidebar pacientes -->
            <div>
                <div class="card p-6" style="padding:1.5rem;">
                    <h2 style="font-family:'Playfair Display',serif; font-size:1.3rem; color:var(--verde); margin-bottom:1rem;">Gestión de Pacientes</h2>
                    <button id="add-patient-btn" class="btn-primary" style="width:100%; margin-bottom:1rem;">+ Agregar Paciente</button>
                    <h3 style="font-size:0.9rem; font-weight:600; color:#666; margin-bottom:0.6rem; text-transform:uppercase; letter-spacing:0.5px;">Lista de Pacientes</h3>
                    <ul id="patient-list" class="space-y-2">
                        <li style="text-align:center; color:#aaa; padding:1.5rem 0; font-size:0.9rem;">No hay pacientes registrados.</li>
                    </ul>
                </div>
            </div>

            <!-- Main content -->
            <div>
                <div style="display:flex; gap:0.5rem; margin-bottom:1.2rem; flex-wrap:wrap;">
                    <button id="tab-patient-details" class="tab-button active">Detalles del Paciente</button>
                    <button id="tab-aggregated-data" class="tab-button">Datos Agregados</button>
                    <button id="tab-scales-format" class="tab-button">Formatos de Escalas</button>
                </div>

                <!-- Patient view -->
                <div id="patient-view">
                    <div id="patient-details-section" class="card" style="padding:1.5rem; display:none;">
                        <div style="display:flex; justify-content:space-between; align-items:flex-start; flex-wrap:wrap; gap:0.8rem;">
                            <div>
                                <h2 id="patient-name-header" style="font-family:'Playfair Display',serif; font-size:1.8rem; color:var(--verde);"></h2>
                                <p id="patient-info-header" style="color:#888; font-size:0.9rem;"></p>
                            </div>
                            <div style="display:flex; gap:0.5rem; flex-wrap:wrap;">
                                <button id="edit-history-btn" class="btn-secondary">Editar Historia</button>
                                <button id="view-history-btn" class="btn-secondary">Ver Historia</button>
                                <button id="add-record-btn" class="btn-primary">+ Medición</button>
                            </div>
                        </div>
                        <hr style="margin:1.2rem 0; border-color:#eee;">
                        <div style="display:grid; grid-template-columns:1fr 1fr; gap:1rem;" id="charts-container">
                            <div class="card" style="padding:1rem;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Fragilidad (SPPB)</h3><div class="chart-container"><canvas id="fragilityChart"></canvas></div></div>
                            <div class="card" style="padding:1rem;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Riesgo de Caída (Up and Go)</h3><div class="chart-container"><canvas id="fallRiskChart"></canvas></div></div>
                            <div class="card" style="padding:1rem;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Cognitiva (Pfeiffer)</h3><div class="chart-container"><canvas id="cognitiveChart"></canvas></div></div>
                            <div class="card" style="padding:1rem;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Adherencia (Morisky)</h3><div class="chart-container"><canvas id="adherenceChart"></canvas></div></div>
                            <div class="card" style="padding:1rem; grid-column:1/-1;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Riesgo Cardiovascular (Framingham %)</h3><div class="chart-container"><canvas id="cardioRiskChart"></canvas></div></div>
                        </div>
                        <div id="records-list-section" style="margin-top:2rem;"></div>
                    </div>
                    <div id="welcome-message" class="card" style="padding:3rem; text-align:center;">
                        <div style="font-size:3rem; margin-bottom:1rem;">🌿</div>
                        <h2 style="font-family:'Playfair Display',serif; font-size:1.4rem; color:var(--verde);">Bienvenido al módulo geriátrico</h2>
                        <p style="color:#888; margin-top:0.5rem; font-size:0.95rem;">Seleccione un paciente o agregue uno nuevo para comenzar el seguimiento.</p>
                    </div>
                </div>

                <!-- Aggregated view -->
                <div id="aggregated-view" style="display:none;">
                    <div class="card" style="padding:1.5rem;">
                        <h2 style="font-family:'Playfair Display',serif; font-size:1.3rem; color:var(--verde); margin-bottom:1rem;">Promedio de Escalas — Todos los Pacientes</h2>
                        <div style="display:grid; grid-template-columns:1fr 1fr; gap:1rem;">
                            <div class="card" style="padding:1rem;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Fragilidad (SPPB)</h3><div class="chart-container"><canvas id="aggFragilityChart"></canvas></div></div>
                            <div class="card" style="padding:1rem;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Riesgo de Caída</h3><div class="chart-container"><canvas id="aggFallRiskChart"></canvas></div></div>
                            <div class="card" style="padding:1rem;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Cognitiva (Pfeiffer)</h3><div class="chart-container"><canvas id="aggCognitiveChart"></canvas></div></div>
                            <div class="card" style="padding:1rem;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Adherencia (Morisky)</h3><div class="chart-container"><canvas id="aggAdherenceChart"></canvas></div></div>
                            <div class="card" style="padding:1rem; grid-column:1/-1;"><h3 style="font-size:0.85rem; font-weight:600; text-align:center; color:#555; margin-bottom:0.5rem;">Riesgo Cardiovascular (%)</h3><div class="chart-container"><canvas id="aggCardioRiskChart"></canvas></div></div>
                        </div>
                    </div>
                </div>

                <!-- Scales format view -->
                <div id="scales-format-view" style="display:none;">
                    <div class="card" style="padding:1.5rem;">
                        <h2 style="font-family:'Playfair Display',serif; font-size:1.3rem; color:var(--verde); margin-bottom:1.2rem;">Formatos de Escalas</h2>
                        <div style="display:flex; flex-direction:column; gap:1.5rem;">
                            <div style="background:#f0faf5; border-radius:12px; padding:1.5rem;">
                                <h3 style="color:var(--verde); font-size:1.1rem; font-weight:700;">Test de Morisky-Green</h3>
                                <p style="color:#555; font-size:0.9rem; margin-top:0.4rem;">Evalúa el cumplimiento del tratamiento farmacológico.</p>
                                <ol style="margin-top:1rem; padding-left:1.2rem; display:flex; flex-direction:column; gap:0.5rem; color:#444; font-size:0.9rem;">
                                    <li>¿Olvida alguna vez tomar los medicamentos? <strong style="color:green;">(Correcta: No)</strong></li>
                                    <li>¿Toma los medicamentos a las horas indicadas? <strong style="color:green;">(Correcta: Sí)</strong></li>
                                    <li>Cuando se encuentra bien, ¿deja de tomar la medicación? <strong style="color:green;">(Correcta: No)</strong></li>
                                    <li>Si alguna vez le sienta mal, ¿deja de tomarla? <strong style="color:green;">(Correcta: No)</strong></li>
                                </ol>
                                <div style="margin-top:1rem; background:#fff; border-radius:8px; padding:1rem; font-size:0.88rem; color:#444;">
                                    <strong>Cumplidor:</strong> Responde correctamente las 4 preguntas (No/Sí/No/No).<br>
                                    <strong style="color:#c00;">Incumplidor:</strong> Cualquier respuesta incorrecta.
                                </div>
                            </div>
                            <div style="background:#fff8f0; border-radius:12px; padding:1.5rem;">
                                <h3 style="color:var(--tierra-oscura); font-size:1.1rem; font-weight:700;">SPPB — Fragilidad</h3>
                                <p style="color:#555; font-size:0.9rem; margin-top:0.4rem;">0–3: Frágil &nbsp;|&nbsp; 4–9: Pre-frágil &nbsp;|&nbsp; 10–12: No frágil</p>
                            </div>
                            <div style="background:#f0f4ff; border-radius:12px; padding:1.5rem;">
                                <h3 style="color:#3346aa; font-size:1.1rem; font-weight:700;">Up and Go — Riesgo de Caída</h3>
                                <p style="color:#555; font-size:0.9rem; margin-top:0.4rem;">Menos de 12 seg: Normal &nbsp;|&nbsp; Más de 12 seg: Riesgo Alto</p>
                            </div>
                            <div style="background:#fef0f0; border-radius:12px; padding:1.5rem;">
                                <h3 style="color:#c00; font-size:1.1rem; font-weight:700;">Pfeiffer — Valoración Cognitiva</h3>
                                <p style="color:#555; font-size:0.9rem; margin-top:0.4rem;">0–2 errores: Normal &nbsp;|&nbsp; 3–4: Leve &nbsp;|&nbsp; 5–7: Moderado &nbsp;|&nbsp; 8–10: Severo</p>
                            </div>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </div>

</div>
</div>

<!-- ══════════════════ FOOTER ══════════════════ -->
<footer>
    <strong>Proyecto Siachoque</strong> — Programa comunitario de atención geriátrica &nbsp;·&nbsp; Boyacá, Colombia &nbsp;·&nbsp; 2025
</footer>

<!-- ══════════════════ MODALS ══════════════════ -->
<div id="patient-modal" class="modal">
    <div class="modal-content" style="max-height:90vh; overflow-y:auto;">
        <span class="close-button" id="close-patient-modal">&times;</span>
        <h2 style="font-family:'Playfair Display',serif; font-size:1.5rem; color:var(--verde); margin-bottom:1.2rem;">Formulario de Historia Clínica</h2>
        <form id="patient-form" style="display:flex; flex-direction:column; gap:1rem;">
            <input type="hidden" id="patient-edit-id">
            <fieldset style="padding:1rem; border-radius:8px;">
                <legend style="padding:0 0.5rem;">Datos de Identificación</legend>
                <div style="display:grid; grid-template-columns:1fr 1fr; gap:0.8rem; margin-top:0.8rem;">
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Nombre Completo</label><input type="text" id="patient-name" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;" required></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Número de Documento</label><input type="text" id="patient-id" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;" required></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Fecha de Nacimiento</label><input type="date" id="patient-birthdate" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;" required></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Lugar de Nacimiento</label><input type="text" id="patient-birthplace" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Dirección</label><input type="text" id="patient-address" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Teléfono</label><input type="tel" id="patient-phone" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Sexo</label><select id="patient-sex" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"><option value="Femenino">Femenino</option><option value="Masculino">Masculino</option></select></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Estado Civil</label><input type="text" id="patient-civil-status" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Ocupación</label><input type="text" id="patient-occupation" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Escolaridad</label><input type="text" id="patient-schooling" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">EAPBS</label><input type="text" id="patient-eapbs" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Régimen</label><input type="text" id="patient-regimen" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div style="grid-column:1/-1;"><label style="font-size:0.85rem; font-weight:600; color:#444;">Estructura Familiar</label><textarea id="patient-family-structure" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                </div>
            </fieldset>

            <fieldset style="padding:1rem; border-radius:8px;">
                <legend style="padding:0 0.5rem;">Consulta Actual</legend>
                <div style="display:flex; flex-direction:column; gap:0.8rem; margin-top:0.8rem;">
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Motivo de Consulta</label><textarea id="patient-consult-reason" rows="3" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Enfermedad Actual</label><textarea id="patient-current-illness" rows="3" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                </div>
            </fieldset>

            <fieldset style="padding:1rem; border-radius:8px;">
                <legend style="padding:0 0.5rem;">Antecedentes</legend>
                <div style="display:grid; grid-template-columns:1fr 1fr; gap:0.8rem; margin-top:0.8rem;">
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Patológicos</label><textarea id="antecedentes-patologicos" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Quirúrgicos</label><textarea id="antecedentes-quirurgicos" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Farmacológicos</label><textarea id="antecedentes-farmacologicos" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Tóxicos</label><textarea id="antecedentes-toxicos" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Familiares</label><textarea id="antecedentes-familiares" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Psiquiátricos</label><textarea id="antecedentes-psiquiatricos" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Transfusionales</label><textarea id="antecedentes-transfusionales" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Hemoclasificación</label><input type="text" id="antecedentes-hemoclasificacion" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Alérgicos</label><textarea id="antecedentes-alergicos" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Ocupacionales</label><textarea id="antecedentes-ocupacionales" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Inmunológicos</label><textarea id="antecedentes-inmunologicos" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">ETS</label><textarea id="antecedentes-ets" rows="2" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></textarea></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Violencia Intrafamiliar</label><select id="antecedentes-vif" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"><option value="No">No</option><option value="Si">Sí</option></select></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">Tipo de Vivienda</label><input type="text" id="patient-housing-type" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                </div>
            </fieldset>

            <fieldset id="ginecologicos-fieldset" style="padding:1rem; border-radius:8px;">
                <legend style="padding:0 0.5rem;">Antecedentes Ginecológicos</legend>
                <div style="display:grid; grid-template-columns:repeat(4, 1fr); gap:0.8rem; margin-top:0.8rem;">
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">FUR</label><input type="date" id="ginecologicos-fur" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">G</label><input type="number" id="ginecologicos-g" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">P</label><input type="number" id="ginecologicos-p" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">V</label><input type="number" id="ginecologicos-v" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">A</label><input type="number" id="ginecologicos-a" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div><label style="font-size:0.85rem; font-weight:600; color:#444;">C</label><input type="number" id="ginecologicos-c" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                    <div style="grid-column:span 2;"><label style="font-size:0.85rem; font-weight:600; color:#444;">Planificación</label><input type="text" id="ginecologicos-planificacion" style="margin-top:0.3rem; width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px;"></div>
                </div>
            </fieldset>

            <button type="submit" class="btn-primary" style="width:100%; padding:0.75rem; font-size:1rem;">Guardar Paciente</button>
        </form>
    </div>
</div>

<div id="record-modal" class="modal">
    <div class="modal-content" style="max-height:90vh; overflow-y:auto;">
        <span class="close-button" id="close-record-modal">&times;</span>
        <h2 style="font-family:'Playfair Display',serif; font-size:1.4rem; color:var(--verde); margin-bottom:1rem;">Nueva Medición — <span id="record-modal-patient-name" style="color:var(--tierra-oscura);"></span></h2>
        <form id="record-form" style="display:flex; flex-direction:column; gap:1rem;">
            <div><label style="font-weight:600; color:#444; font-size:0.9rem;">Fecha de Medición</label><input type="date" id="record-date" style="width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px; margin-top:0.3rem;" required></div>
            <div style="border:1px solid #eee; padding:0.8rem; border-radius:8px;"><label style="font-weight:700; color:var(--verde); font-size:0.9rem;">Fragilidad SPPB (0–12)</label><input type="number" step="any" id="fragility-score" min="0" max="12" style="width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px; margin-top:0.4rem;" required><p style="font-size:0.78rem; color:#888; margin-top:0.3rem;">0–3 Frágil · 4–9 Pre-frágil · 10–12 No frágil</p></div>
            <div style="border:1px solid #eee; padding:0.8rem; border-radius:8px;"><label style="font-weight:700; color:var(--verde); font-size:0.9rem;">Up and Go (segundos)</label><input type="number" step="any" id="fall-risk-score" min="0" style="width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px; margin-top:0.4rem;" required><p style="font-size:0.78rem; color:#888; margin-top:0.3rem;">&gt;12 seg = Riesgo Alto</p></div>
            <div style="border:1px solid #eee; padding:0.8rem; border-radius:8px;"><label style="font-weight:700; color:var(--verde); font-size:0.9rem;">Pfeiffer — Errores (0–10)</label><input type="number" step="any" id="cognitive-score" min="0" max="10" style="width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px; margin-top:0.4rem;" required><p style="font-size:0.78rem; color:#888; margin-top:0.3rem;">0–2 Normal · 3–4 Leve · 5–7 Moderado · 8–10 Severo</p></div>
            <fieldset style="padding:0.8rem; border-radius:8px; border:1px solid #eee;">
                <legend style="padding:0 0.4rem; font-size:0.9rem;">Test de Morisky-Green</legend>
                <div style="display:flex; flex-direction:column; gap:0.8rem; margin-top:0.6rem;" id="morisky-form">
                    <div><p style="font-size:0.88rem; color:#333;">1. ¿Olvida alguna vez tomar los medicamentos?</p><div style="display:flex; gap:0.5rem; margin-top:0.3rem;"><input type="radio" name="morisky-q1" value="si" id="morisky-q1-si" class="sr-only morisky-radio"><label for="morisky-q1-si" class="morisky-label">Sí</label><input type="radio" name="morisky-q1" value="no" id="morisky-q1-no" class="sr-only morisky-radio"><label for="morisky-q1-no" class="morisky-label">No</label></div></div>
                    <div><p style="font-size:0.88rem; color:#333;">2. ¿Toma los medicamentos a las horas indicadas?</p><div style="display:flex; gap:0.5rem; margin-top:0.3rem;"><input type="radio" name="morisky-q2" value="si" id="morisky-q2-si" class="sr-only morisky-radio"><label for="morisky-q2-si" class="morisky-label">Sí</label><input type="radio" name="morisky-q2" value="no" id="morisky-q2-no" class="sr-only morisky-radio"><label for="morisky-q2-no" class="morisky-label">No</label></div></div>
                    <div><p style="font-size:0.88rem; color:#333;">3. Cuando se encuentra bien, ¿deja de tomar la medicación?</p><div style="display:flex; gap:0.5rem; margin-top:0.3rem;"><input type="radio" name="morisky-q3" value="si" id="morisky-q3-si" class="sr-only morisky-radio"><label for="morisky-q3-si" class="morisky-label">Sí</label><input type="radio" name="morisky-q3" value="no" id="morisky-q3-no" class="sr-only morisky-radio"><label for="morisky-q3-no" class="morisky-label">No</label></div></div>
                    <div><p style="font-size:0.88rem; color:#333;">4. Si alguna vez le sienta mal, ¿deja de tomarla?</p><div style="display:flex; gap:0.5rem; margin-top:0.3rem;"><input type="radio" name="morisky-q4" value="si" id="morisky-q4-si" class="sr-only morisky-radio"><label for="morisky-q4-si" class="morisky-label">Sí</label><input type="radio" name="morisky-q4" value="no" id="morisky-q4-no" class="sr-only morisky-radio"><label for="morisky-q4-no" class="morisky-label">No</label></div></div>
                </div>
                <div id="morisky-result" style="margin-top:0.8rem; padding:0.6rem; background:#f5f5f5; border-radius:8px; text-align:center; font-weight:600; font-size:0.88rem; color:#555;">Seleccione una respuesta para cada pregunta.</div>
                <input type="hidden" id="adherence-score" required>
            </fieldset>
            <div style="border:1px solid #eee; padding:0.8rem; border-radius:8px;"><label style="font-weight:700; color:var(--verde); font-size:0.9rem;">Framingham — Riesgo Cardiovascular (%)</label><input type="number" step="any" id="cardio-risk-score" min="0" max="100" style="width:100%; padding:0.5rem; border:1px solid #ddd; border-radius:6px; margin-top:0.4rem;" required><p style="font-size:0.78rem; color:#888; margin-top:0.3rem;">&lt;10% Bajo · 10–20% Moderado · &gt;20% Alto</p></div>
            <button type="submit" class="btn-primary" style="width:100%; padding:0.75rem; font-size:1rem;">Guardar Medición</button>
        </form>
    </div>
</div>

<div id="confirm-modal" class="modal">
    <div class="modal-content" style="text-align:center; max-width:420px;">
        <h2 style="font-size:1.2rem; font-weight:700; margin-bottom:1rem;">Confirmar Eliminación</h2>
        <p id="confirm-modal-text" style="color:#555; margin-bottom:1.5rem; font-size:0.95rem;"></p>
        <div style="display:flex; justify-content:center; gap:0.8rem;">
            <button id="confirm-modal-cancel" class="btn-secondary">Cancelar</button>
            <button id="confirm-modal-confirm" class="btn-danger" style="padding:0.55rem 1.2rem; font-size:0.9rem;">Confirmar</button>
        </div>
    </div>
</div>

<div id="history-modal" class="modal">
    <div class="modal-content" style="max-height:90vh; overflow-y:auto;">
        <span class="close-button" id="close-history-modal">&times;</span>
        <h2 style="font-family:'Playfair Display',serif; font-size:1.4rem; color:var(--verde); margin-bottom:1rem;">Historia Clínica — <span id="history-patient-name" style="color:var(--tierra-oscura);"></span></h2>
        <div id="history-content" style="display:flex; flex-direction:column; gap:1rem;"></div>
    </div>
</div>

<!-- ══════════════════ JAVASCRIPT ══════════════════ -->
<script>
document.addEventListener('DOMContentLoaded', () => {

    // ─── NAVEGACIÓN PRINCIPAL ─── //
    document.querySelectorAll('.nav-tab').forEach(tab => {
        tab.addEventListener('click', () => {
            document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.page-section').forEach(s => s.classList.remove('active'));
            tab.classList.add('active');
            document.getElementById(tab.dataset.target).classList.add('active');
        });
    });

    // ─── GALERÍA DE IMÁGENES ─── //
    const fileInput = document.getElementById('file-input');
    const uploadArea = document.getElementById('upload-area');
    const galleryGrid = document.getElementById('gallery-grid');
    const galleryEmpty = document.getElementById('gallery-empty');

    const updateGalleryEmpty = () => {
        galleryEmpty.style.display = galleryGrid.children.length === 0 ? 'block' : 'none';
    };

    const addImageToGallery = (src) => {
        const item = document.createElement('div');
        item.className = 'gallery-item';
        item.innerHTML = `<img src="${src}" alt="Imagen del proyecto"><button class="delete-img" title="Eliminar">✕</button>`;
        item.querySelector('.delete-img').addEventListener('click', () => {
            item.remove();
            updateGalleryEmpty();
        });
        galleryGrid.appendChild(item);
        updateGalleryEmpty();
    };

    fileInput.addEventListener('change', (e) => {
        Array.from(e.target.files).forEach(file => {
            const reader = new FileReader();
            reader.onload = ev => addImageToGallery(ev.target.result);
            reader.readAsDataURL(file);
        });
        fileInput.value = '';
    });

    uploadArea.addEventListener('dragover', (e) => { e.preventDefault(); uploadArea.classList.add('drag-over'); });
    uploadArea.addEventListener('dragleave', () => uploadArea.classList.remove('drag-over'));
    uploadArea.addEventListener('drop', (e) => {
        e.preventDefault();
        uploadArea.classList.remove('drag-over');
        Array.from(e.dataTransfer.files).filter(f => f.type.startsWith('image/')).forEach(file => {
            const reader = new FileReader();
            reader.onload = ev => addImageToGallery(ev.target.result);
            reader.readAsDataURL(file);
        });
    });

    // ─── MÓDULO GERIÁTRICO ─── //
    let patients = JSON.parse(localStorage.getItem('patients_siachoque')) || [];
    let selectedPatientId = null;
    const charts = {};
    let confirmCallback = null;

    const DOM = {
        addPatientBtn: document.getElementById('add-patient-btn'),
        patientModal: document.getElementById('patient-modal'),
        closePatientModal: document.getElementById('close-patient-modal'),
        patientForm: document.getElementById('patient-form'),
        patientList: document.getElementById('patient-list'),
        welcomeMessage: document.getElementById('welcome-message'),
        patientDetailsSection: document.getElementById('patient-details-section'),
        addRecordBtn: document.getElementById('add-record-btn'),
        recordModal: document.getElementById('record-modal'),
        closeRecordModal: document.getElementById('close-record-modal'),
        recordForm: document.getElementById('record-form'),
        recordsListSection: document.getElementById('records-list-section'),
        confirmModal: document.getElementById('confirm-modal'),
        confirmModalText: document.getElementById('confirm-modal-text'),
        confirmModalConfirm: document.getElementById('confirm-modal-confirm'),
        confirmModalCancel: document.getElementById('confirm-modal-cancel'),
        tabPatientDetails: document.getElementById('tab-patient-details'),
        tabAggregatedData: document.getElementById('tab-aggregated-data'),
        tabScalesFormat: document.getElementById('tab-scales-format'),
        patientView: document.getElementById('patient-view'),
        aggregatedView: document.getElementById('aggregated-view'),
        scalesFormatView: document.getElementById('scales-format-view'),
        viewHistoryBtn: document.getElementById('view-history-btn'),
        editHistoryBtn: document.getElementById('edit-history-btn'),
        historyModal: document.getElementById('history-modal'),
        closeHistoryModal: document.getElementById('close-history-modal'),
        historyPatientName: document.getElementById('history-patient-name'),
        historyContent: document.getElementById('history-content'),
        ginecologicosFieldset: document.getElementById('ginecologicos-fieldset'),
        patientSexSelect: document.getElementById('patient-sex'),
        patientEditId: document.getElementById('patient-edit-id'),
        moriskyForm: document.getElementById('morisky-form'),
        moriskyResult: document.getElementById('morisky-result'),
        adherenceScoreInput: document.getElementById('adherence-score'),
    };

    const saveData = () => localStorage.setItem('patients_siachoque', JSON.stringify(patients));
    const calculateAge = (birthdate) => {
        const b = new Date(birthdate), today = new Date();
        let age = today.getFullYear() - b.getFullYear();
        const m = today.getMonth() - b.getMonth();
        if (m < 0 || (m === 0 && today.getDate() < b.getDate())) age--;
        return age;
    };

    const openConfirmModal = (text, cb) => { DOM.confirmModalText.textContent = text; confirmCallback = cb; DOM.confirmModal.style.display = 'flex'; };
    const closeConfirmModal = () => { DOM.confirmModal.style.display = 'none'; confirmCallback = null; };

    const getPatientDataFromForm = () => ({
        id: document.getElementById('patient-id').value,
        name: document.getElementById('patient-name').value,
        birthdate: document.getElementById('patient-birthdate').value,
        sex: DOM.patientSexSelect.value,
        history: {
            birthplace: document.getElementById('patient-birthplace').value,
            address: document.getElementById('patient-address').value,
            phone: document.getElementById('patient-phone').value,
            civilStatus: document.getElementById('patient-civil-status').value,
            occupation: document.getElementById('patient-occupation').value,
            schooling: document.getElementById('patient-schooling').value,
            eapbs: document.getElementById('patient-eapbs').value,
            regimen: document.getElementById('patient-regimen').value,
            familyStructure: document.getElementById('patient-family-structure').value,
            consultReason: document.getElementById('patient-consult-reason').value,
            currentIllness: document.getElementById('patient-current-illness').value,
            housingType: document.getElementById('patient-housing-type').value,
            antecedentes: {
                patologicos: document.getElementById('antecedentes-patologicos').value,
                quirurgicos: document.getElementById('antecedentes-quirurgicos').value,
                farmacologicos: document.getElementById('antecedentes-farmacologicos').value,
                toxicos: document.getElementById('antecedentes-toxicos').value,
                familiares: document.getElementById('antecedentes-familiares').value,
                psiquiatricos: document.getElementById('antecedentes-psiquiatricos').value,
                transfusionales: document.getElementById('antecedentes-transfusionales').value,
                hemoclasificacion: document.getElementById('antecedentes-hemoclasificacion').value,
                alergicos: document.getElementById('antecedentes-alergicos').value,
                ocupacionales: document.getElementById('antecedentes-ocupacionales').value,
                inmunologicos: document.getElementById('antecedentes-inmunologicos').value,
                ets: document.getElementById('antecedentes-ets').value,
                vif: document.getElementById('antecedentes-vif').value,
            },
            ginecologicos: {
                fur: document.getElementById('ginecologicos-fur').value,
                g: document.getElementById('ginecologicos-g').value,
                p: document.getElementById('ginecologicos-p').value,
                v: document.getElementById('ginecologicos-v').value,
                a: document.getElementById('ginecologicos-a').value,
                c: document.getElementById('ginecologicos-c').value,
                planificacion: document.getElementById('ginecologicos-planificacion').value,
            }
        }
    });

    const populatePatientForm = (patient) => {
        document.getElementById('patient-id').value = patient.id;
        document.getElementById('patient-name').value = patient.name;
        document.getElementById('patient-birthdate').value = patient.birthdate;
        DOM.patientSexSelect.value = patient.sex;
        const h = patient.history;
        ['birthplace','address','phone','civilStatus','occupation','schooling','eapbs','regimen','familyStructure','consultReason','currentIllness','housingType'].forEach(k => {
            const el = document.getElementById('patient-' + k.replace(/([A-Z])/g, '-$1').toLowerCase());
            if (el) el.value = h[k] || '';
        });
        document.getElementById('patient-family-structure').value = h.familyStructure || '';
        document.getElementById('patient-consult-reason').value = h.consultReason || '';
        document.getElementById('patient-current-illness').value = h.currentIllness || '';
        document.getElementById('patient-housing-type').value = h.housingType || '';
        const a = h.antecedentes;
        Object.keys(a).forEach(k => { const el = document.getElementById('antecedentes-' + k); if (el) el.value = a[k] || ''; });
        const g = h.ginecologicos;
        DOM.ginecologicosFieldset.style.display = patient.sex === 'Femenino' ? 'block' : 'none';
        Object.keys(g).forEach(k => { const el = document.getElementById('ginecologicos-' + k); if (el) el.value = g[k] || ''; });
    };

    const calculateMoriskyScore = () => {
        const q1 = DOM.moriskyForm.querySelector('input[name="morisky-q1"]:checked');
        const q2 = DOM.moriskyForm.querySelector('input[name="morisky-q2"]:checked');
        const q3 = DOM.moriskyForm.querySelector('input[name="morisky-q3"]:checked');
        const q4 = DOM.moriskyForm.querySelector('input[name="morisky-q4"]:checked');
        if (!q1 || !q2 || !q3 || !q4) { DOM.moriskyResult.textContent = 'Seleccione una respuesta para cada pregunta.'; DOM.adherenceScoreInput.value = ''; return; }
        let score = 0;
        if (q1.value === 'si') score++;
        if (q2.value === 'no') score++;
        if (q3.value === 'si') score++;
        if (q4.value === 'si') score++;
        DOM.adherenceScoreInput.value = score;
        if (score === 0) {
            DOM.moriskyResult.style.background = '#d8f3dc'; DOM.moriskyResult.style.color = '#1b4332';
            DOM.moriskyResult.innerHTML = '✅ <strong>Cumple</strong> con el tratamiento';
        } else {
            DOM.moriskyResult.style.background = '#fde8e8'; DOM.moriskyResult.style.color = '#c00';
            DOM.moriskyResult.innerHTML = `❌ <strong>No Cumple</strong> — Puntaje de incumplimiento: ${score}`;
        }
    };

    const renderPatientList = () => {
        DOM.patientList.innerHTML = '';
        if (patients.length === 0) {
            DOM.patientList.innerHTML = '<li style="text-align:center; color:#bbb; padding:1.5rem 0; font-size:0.88rem;">No hay pacientes registrados.</li>';
            return;
        }
        patients.forEach(patient => {
            const age = calculateAge(patient.birthdate);
            const li = document.createElement('li');
            li.style.cssText = 'display:flex; justify-content:space-between; align-items:center; padding:0.65rem 0.8rem; border-radius:8px; cursor:pointer; transition:background 0.15s;';
            li.className = `patient-list-item ${patient.id === selectedPatientId ? 'active' : ''}`;
            li.dataset.id = patient.id;
            li.innerHTML = `<div><p style="font-weight:600; color:#333; font-size:0.9rem;">${patient.name}</p><p style="font-size:0.78rem; color:#888;">Doc: ${patient.id} · ${age} años</p></div><button class="btn-danger delete-patient-btn" data-id="${patient.id}" style="flex-shrink:0;">✕</button>`;
            li.addEventListener('click', (e) => {
                if (e.target.classList.contains('delete-patient-btn')) return;
                selectedPatientId = patient.id; renderPatientDetails(); renderPatientList();
            });
            DOM.patientList.appendChild(li);
        });
        document.querySelectorAll('.delete-patient-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                e.stopPropagation();
                const pid = e.target.dataset.id;
                const pat = patients.find(p => p.id === pid);
                openConfirmModal(`¿Eliminar a ${pat.name}? Esta acción no se puede deshacer.`, () => {
                    patients = patients.filter(p => p.id !== pid);
                    if (selectedPatientId === pid) selectedPatientId = null;
                    saveData(); renderPatientList(); renderPatientDetails(); renderAggregatedCharts(); closeConfirmModal();
                });
            });
        });
    };

    const renderPatientDetails = () => {
        if (!selectedPatientId) {
            DOM.welcomeMessage.style.display = 'block';
            DOM.patientDetailsSection.style.display = 'none';
            return;
        }
        const patient = patients.find(p => p.id === selectedPatientId);
        if (patient) {
            DOM.welcomeMessage.style.display = 'none';
            DOM.patientDetailsSection.style.display = 'block';
            document.getElementById('patient-name-header').textContent = patient.name;
            document.getElementById('patient-info-header').textContent = `Doc: ${patient.id} · ${calculateAge(patient.birthdate)} años · ${patient.sex}`;
            document.getElementById('record-modal-patient-name').textContent = patient.name;
            renderAllCharts(patient);
            renderRecordsList(patient);
        }
    };

    const renderRecordsList = (patient) => {
        DOM.recordsListSection.innerHTML = '<h3 style="font-family:\'Playfair Display\',serif; font-size:1.1rem; color:var(--verde); margin-bottom:1rem;">Historial de Mediciones</h3>';
        if (!patient.records || patient.records.length === 0) {
            DOM.recordsListSection.innerHTML += '<p style="color:#aaa; font-size:0.9rem;">No hay mediciones registradas.</p>';
            return;
        }
        const table = document.createElement('table');
        table.style.cssText = 'width:100%; border-collapse:collapse; font-size:0.85rem;';
        table.innerHTML = `<thead><tr style="background:#f0faf5;"><th style="padding:0.5rem; border:1px solid #ddd; color:var(--verde);">Fecha</th><th style="padding:0.5rem; border:1px solid #ddd; color:var(--verde);">Frag.</th><th style="padding:0.5rem; border:1px solid #ddd; color:var(--verde);">Caída</th><th style="padding:0.5rem; border:1px solid #ddd; color:var(--verde);">Cogn.</th><th style="padding:0.5rem; border:1px solid #ddd; color:var(--verde);">Adher.</th><th style="padding:0.5rem; border:1px solid #ddd; color:var(--verde);">Cardio.</th><th style="padding:0.5rem; border:1px solid #ddd;">Acción</th></tr></thead><tbody></tbody>`;
        const tbody = table.querySelector('tbody');
        patient.records.forEach((rec, idx) => {
            const tr = document.createElement('tr');
            tr.innerHTML = `<td style="padding:0.45rem; border:1px solid #eee;">${new Date(rec.date).toLocaleDateString('es-ES')}</td><td style="padding:0.45rem; border:1px solid #eee; text-align:center;">${rec.fragility}</td><td style="padding:0.45rem; border:1px solid #eee; text-align:center;">${rec.fallRisk}s</td><td style="padding:0.45rem; border:1px solid #eee; text-align:center;">${rec.cognitive}</td><td style="padding:0.45rem; border:1px solid #eee; text-align:center;">${rec.adherence === 0 ? '✅' : `❌(${rec.adherence})`}</td><td style="padding:0.45rem; border:1px solid #eee; text-align:center;">${rec.cardioRisk}%</td><td style="padding:0.45rem; border:1px solid #eee; text-align:center;"><button class="btn-danger delete-record-btn" data-index="${idx}">Eliminar</button></td>`;
            tbody.appendChild(tr);
        });
        DOM.recordsListSection.appendChild(table);
        document.querySelectorAll('.delete-record-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const idx = parseInt(e.target.dataset.index, 10);
                openConfirmModal('¿Eliminar esta medición?', () => {
                    patient.records.splice(idx, 1);
                    saveData(); renderPatientDetails(); renderAggregatedCharts(); closeConfirmModal();
                });
            });
        });
    };

    const createOrUpdateChart = (chartId, label, labels, data, color) => {
        const ctx = document.getElementById(chartId).getContext('2d');
        if (charts[chartId]) charts[chartId].destroy();
        charts[chartId] = new Chart(ctx, {
            type: 'line',
            data: { labels, datasets: [{ label, data, borderColor: color, backgroundColor: color + '22', tension: 0.3, fill: true, pointBackgroundColor: color, pointRadius: 4 }] },
            options: { responsive: true, maintainAspectRatio: false, scales: { y: { beginAtZero: true, grid: { color: '#f0f0f0' } }, x: { grid: { display: false } } }, plugins: { legend: { display: false } } }
        });
    };

    const scalesDef = [
        { key: 'fragility', chartId: 'fragilityChart', aggId: 'aggFragilityChart', label: 'Fragilidad', color: '#2d6a4f' },
        { key: 'fallRisk', chartId: 'fallRiskChart', aggId: 'aggFallRiskChart', label: 'Up & Go (seg)', color: '#40916c' },
        { key: 'cognitive', chartId: 'cognitiveChart', aggId: 'aggCognitiveChart', label: 'Pfeiffer errores', color: '#dda15e' },
        { key: 'adherence', chartId: 'adherenceChart', aggId: 'aggAdherenceChart', label: 'Morisky', color: '#bc6c25' },
        { key: 'cardioRisk', chartId: 'cardioRiskChart', aggId: 'aggCardioRiskChart', label: 'Framingham %', color: '#c1121f' }
    ];

    const renderAllCharts = (patient) => {
        scalesDef.forEach(s => {
            const recs = (patient.records || []).slice().sort((a, b) => new Date(a.date) - new Date(b.date));
            createOrUpdateChart(s.chartId, s.label, recs.map(r => new Date(r.date).toLocaleDateString('es-ES')), recs.map(r => r[s.key]), s.color);
        });
    };

    const renderAggregatedCharts = () => {
        const allRecs = patients.flatMap(p => p.records || []);
        if (!allRecs.length) return;
        const byDate = {};
        allRecs.forEach(rec => {
            if (!byDate[rec.date]) byDate[rec.date] = { fragility:[], fallRisk:[], cognitive:[], adherence:[], cardioRisk:[] };
            scalesDef.forEach(s => { if (rec[s.key] !== undefined) byDate[rec.date][s.key].push(rec[s.key]); });
        });
        const dates = Object.keys(byDate).sort((a,b) => new Date(a)-new Date(b));
        const avg = arr => arr.length ? arr.reduce((a,b) => a+b, 0) / arr.length : 0;
        scalesDef.forEach(s => {
            createOrUpdateChart(s.aggId, 'Promedio ' + s.label, dates.map(d => new Date(d).toLocaleDateString('es-ES')), dates.map(d => +avg(byDate[d][s.key]).toFixed(2)), s.color);
        });
    };

    const renderHistoryModal = (patient) => {
        DOM.historyPatientName.textContent = patient.name;
        const row = (label, value) => `<div style="display:grid; grid-template-columns:1fr 2fr; gap:0.5rem; padding:0.4rem 0; border-bottom:1px solid #f0f0f0;"><span style="font-size:0.82rem; font-weight:600; color:#888;">${label}</span><span style="font-size:0.88rem; color:#333;">${value || '—'}</span></div>`;
        const h = patient.history, a = h.antecedentes, g = h.ginecologicos;
        DOM.historyContent.innerHTML = `
            <div style="background:#f0faf5; border-radius:10px; padding:1rem;">
                <h3 style="color:var(--verde); font-weight:700; margin-bottom:0.6rem;">Identificación</h3>
                ${row('Nombre', patient.name)}${row('Documento', patient.id)}${row('Nacimiento', patient.birthdate)}${row('Lugar', h.birthplace)}${row('Dirección', h.address)}${row('Teléfono', h.phone)}${row('Sexo', patient.sex)}${row('Estado Civil', h.civilStatus)}${row('Ocupación', h.occupation)}${row('Escolaridad', h.schooling)}${row('EAPBS', h.eapbs)}${row('Régimen', h.regimen)}${row('Fam. Estructura', h.familyStructure)}
            </div>
            <div style="background:#fff8f0; border-radius:10px; padding:1rem;">
                <h3 style="color:var(--tierra-oscura); font-weight:700; margin-bottom:0.6rem;">Consulta Actual</h3>
                ${row('Motivo', h.consultReason)}${row('Enf. Actual', h.currentIllness)}
            </div>
            <div style="background:#f5f5f5; border-radius:10px; padding:1rem;">
                <h3 style="color:#444; font-weight:700; margin-bottom:0.6rem;">Antecedentes</h3>
                ${Object.entries(a).map(([k,v]) => row(k.charAt(0).toUpperCase()+k.slice(1), v)).join('')}${row('Tipo Vivienda', h.housingType)}
            </div>
            ${patient.sex === 'Femenino' ? `<div style="background:#fdf0f8; border-radius:10px; padding:1rem;"><h3 style="color:#9b2c7e; font-weight:700; margin-bottom:0.6rem;">Ginecológicos</h3>${Object.entries(g).map(([k,v]) => row(k.toUpperCase(), v)).join('')}</div>` : ''}
        `;
        DOM.historyModal.style.display = 'flex';
    };

    // ─── EVENT LISTENERS ─── //
    DOM.addPatientBtn.addEventListener('click', () => {
        DOM.patientForm.reset(); DOM.patientEditId.value = '';
        DOM.ginecologicosFieldset.style.display = 'block';
        DOM.patientModal.style.display = 'flex';
    });
    DOM.closePatientModal.addEventListener('click', () => DOM.patientModal.style.display = 'none');

    DOM.patientForm.addEventListener('submit', (e) => {
        e.preventDefault();
        const data = getPatientDataFromForm();
        const editId = DOM.patientEditId.value;
        if (editId) {
            const idx = patients.findIndex(p => p.id === editId);
            if (idx !== -1) patients[idx] = { ...data, records: patients[idx].records };
        } else {
            if (patients.some(p => p.id === data.id)) { alert('Ya existe un paciente con este documento.'); return; }
            patients.push({ ...data, records: [] });
        }
        saveData(); renderPatientList(); if (editId) renderPatientDetails();
        DOM.patientModal.style.display = 'none';
    });

    DOM.addRecordBtn.addEventListener('click', () => {
        if (!selectedPatientId) return;
        DOM.recordForm.reset();
        document.getElementById('record-date').valueAsDate = new Date();
        DOM.moriskyResult.textContent = 'Seleccione una respuesta para cada pregunta.';
        DOM.moriskyResult.style.background = '#f5f5f5'; DOM.moriskyResult.style.color = '#555';
        DOM.adherenceScoreInput.value = '';
        DOM.recordModal.style.display = 'flex';
    });
    DOM.closeRecordModal.addEventListener('click', () => DOM.recordModal.style.display = 'none');

    DOM.recordForm.addEventListener('submit', (e) => {
        e.preventDefault();
        const patient = patients.find(p => p.id === selectedPatientId);
        if (patient) {
            const rec = {
                date: document.getElementById('record-date').value,
                fragility: parseFloat(document.getElementById('fragility-score').value),
                fallRisk: parseFloat(document.getElementById('fall-risk-score').value),
                cognitive: parseFloat(document.getElementById('cognitive-score').value),
                adherence: parseFloat(document.getElementById('adherence-score').value),
                cardioRisk: parseFloat(document.getElementById('cardio-risk-score').value)
            };
            if (!patient.records) patient.records = [];
            patient.records.push(rec);
            saveData(); renderPatientDetails(); renderAggregatedCharts();
            DOM.recordModal.style.display = 'none';
        }
    });

    DOM.confirmModalCancel.addEventListener('click', closeConfirmModal);
    DOM.confirmModalConfirm.addEventListener('click', () => { if (confirmCallback) confirmCallback(); });
    DOM.moriskyForm.addEventListener('change', calculateMoriskyScore);

    DOM.tabPatientDetails.addEventListener('click', () => {
        DOM.patientView.style.display = 'block'; DOM.aggregatedView.style.display = 'none'; DOM.scalesFormatView.style.display = 'none';
        [DOM.tabPatientDetails, DOM.tabAggregatedData, DOM.tabScalesFormat].forEach((t,i) => t.classList.toggle('active', i===0));
    });
    DOM.tabAggregatedData.addEventListener('click', () => {
        DOM.patientView.style.display = 'none'; DOM.aggregatedView.style.display = 'block'; DOM.scalesFormatView.style.display = 'none';
        [DOM.tabPatientDetails, DOM.tabAggregatedData, DOM.tabScalesFormat].forEach((t,i) => t.classList.toggle('active', i===1));
        renderAggregatedCharts();
    });
    DOM.tabScalesFormat.addEventListener('click', () => {
        DOM.patientView.style.display = 'none'; DOM.aggregatedView.style.display = 'none'; DOM.scalesFormatView.style.display = 'block';
        [DOM.tabPatientDetails, DOM.tabAggregatedData, DOM.tabScalesFormat].forEach((t,i) => t.classList.toggle('active', i===2));
    });

    DOM.viewHistoryBtn.addEventListener('click', () => {
        const p = patients.find(p => p.id === selectedPatientId); if (p) renderHistoryModal(p);
    });
    DOM.editHistoryBtn.addEventListener('click', () => {
        const p = patients.find(p => p.id === selectedPatientId);
        if (p) { DOM.patientForm.reset(); DOM.patientEditId.value = p.id; populatePatientForm(p); DOM.patientModal.style.display = 'flex'; }
    });
    DOM.closeHistoryModal.addEventListener('click', () => DOM.historyModal.style.display = 'none');

    DOM.patientSexSelect.addEventListener('change', (e) => {
        DOM.ginecologicosFieldset.style.display = e.target.value === 'Femenino' ? 'block' : 'none';
    });

    window.addEventListener('click', (e) => {
        if (e.target === DOM.patientModal) DOM.patientModal.style.display = 'none';
        if (e.target === DOM.recordModal) DOM.recordModal.style.display = 'none';
        if (e.target === DOM.confirmModal) closeConfirmModal();
        if (e.target === DOM.historyModal) DOM.historyModal.style.display = 'none';
    });

    // Init
    renderPatientList();
    renderPatientDetails();
});
</script>
</body>
</html>
    </script>
</body>
</html>
