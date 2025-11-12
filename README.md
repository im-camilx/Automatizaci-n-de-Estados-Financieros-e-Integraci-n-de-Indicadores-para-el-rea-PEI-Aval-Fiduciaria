<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Automatización de Estados Financieros — Aval Fiduciaria</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.js"></script>
  <link href="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.css" rel="stylesheet" />
  <style>
    body {font-family:'Inter', sans-serif; margin:0; background:linear-gradient(120deg,#030b1b 0%,#081c36 100%); color:#e6eef6; overflow-x:hidden;}
    /* header: oscuro por defecto; solo el recuadro del logo será blanco */
    header {text-align:center; margin-bottom:50px; padding-top:30px; position:relative;}
    header .logo-box {position:absolute; top:18px; left:30px; background:white; padding:8px; border-radius:10px; box-shadow:0 6px 18px rgba(0,0,0,0.4);}
    header .logo-box img{width:180px; display:block}
    header h1 {font-size:38px; margin-bottom:10px; color:#00d4ff; text-shadow:0 0 10px rgba(0,212,255,0.12); animation:fadeInDown 1.2s ease-in-out;}
    header p {color:#9aa4b2; font-size:16px; margin-bottom:10px;}
    .team {display:flex; flex-wrap:wrap; justify-content:center; gap:14px; margin-top:10px;}
    .member {background:linear-gradient(90deg,#00d4ff,#0084ff); color:white; border-radius:50px; padding:10px 20px; font-weight:600; transition:transform 0.3s;}
    .member:hover {transform:scale(1.05);}

    .nav {position:sticky; top:0; background:rgba(0,0,0,0.8); backdrop-filter:blur(8px); display:flex; justify-content:center; gap:20px; padding:12px 0; z-index:10;}
    .nav a {color:#e6eef6; text-decoration:none; font-weight:600; transition:color 0.3s;}
    .nav a:hover {color:#00d4ff;}

    .grid {display:grid; grid-template-columns:repeat(auto-fit,minmax(380px,1fr)); gap:20px; margin-top:20px;}
    section {background:rgba(255,255,255,0.04); border-radius:14px; padding:24px; box-shadow:0 4px 20px rgba(0,0,0,0.4); margin:20px; transition:transform 0.3s, background 0.3s;}
    section:hover {transform:translateY(-6px); background:rgba(255,255,255,0.07);}

    h2 {color:#00d4ff; font-size:22px; border-left:4px solid #00d4ff; padding-left:10px; margin-bottom:10px;}
    p,li {font-size:15px; line-height:1.6; color:#d1d5db;}
    ul {margin-left:20px;}

    canvas {max-width:100%; height:250px; margin-top:10px;}

    .legend {display:flex; justify-content:center; gap:20px; margin:10px 0; flex-wrap:wrap;}
    .legend-item {display:flex; align-items:center; gap:6px;}
    .color-box {width:14px; height:14px; border-radius:3px;}

    .kanban {display:flex; gap:20px; justify-content:space-around; flex-wrap:wrap;}
    .kanban-column {border-radius:10px; width:30%; min-width:250px; padding:10px; color:white;}
    .kanban-column:nth-child(1){background:linear-gradient(180deg,#ffb703,#fb8500);} /* Pendiente */
    .kanban-column:nth-child(2){background:linear-gradient(180deg,#219ebc,#023047);} /* En progreso */
    .kanban-column:nth-child(3){background:linear-gradient(180deg,#00b4d8,#0077b6);} /* Completado */
    .kanban h3 {border-bottom:1px solid rgba(255,255,255,0.2); padding-bottom:5px;}
    .task {background:rgba(255,255,255,0.15); margin:8px 0; padding:10px; border-radius:6px;}

    .example-note {font-size:12px; color:#9aa4b2; text-align:center; margin-top:8px;}

    footer {text-align:center; font-size:14px; color:#9aa4b2; margin:40px 0;}

    @keyframes fadeInDown {from{opacity:0;transform:translateY(-20px);}to{opacity:1;transform:translateY(0);}}
  </style>
</head>
<body>
  <div class="nav">
    <a href="#resumen">Resumen</a>
    <a href="#objetivos">Objetivos</a>
    <a href="#resultados">Resultados</a>
    <a href="#indicadores">Indicadores</a>
    <a href="#metodologia">Metodología</a>
    <a href="#impacto">Impacto</a>
    <a href="#kanban">Kanban</a>
    <a href="#beneficios">Beneficios</a>
    <a href="#conclusiones">Conclusiones</a>
  </div>

  <header>
    <div class="logo-box" aria-hidden="true"><img src="logo.jpg.png" alt="Logo Aval Fiduciaria"></div>
    <h1 data-aos="fade-down">Automatización de Estados Financieros e Integración de Indicadores</h1>
    <p data-aos="fade-up">Proyecto de Excelencia</p>
    <p data-aos="fade-up">Universidad de Los Andes | Corficolombiana</p>
    <div class="team" data-aos="zoom-in">
      <div class="member">Juan Camilo Posso Murillo</div>
      <div class="member">Kelin Lorena Ortiz Rojas</div>
      <div class="member">Laura Ximena Arias Vásquez</div>
      <div class="member">Yamileth Sánchez</div>
      <div class="member">Yeison Samuel Parra Cuéllar</div>
    </div>
  </header>

  <main class="grid">
    <section id="resumen" data-aos="fade-up">
      <h2>Resumen Ejecutivo</h2>
      <p>Proyecto de optimización del proceso contable en Aval Fiduciaria mediante automatización, uso de Power Query, macros y análisis financiero inteligente. Mejora la precisión, reduce tiempos y fortalece la toma de decisiones.</p>
      <canvas id="chartResumen"></canvas>
      <div class="legend">
        <div class="legend-item"><div class="color-box" style="background:#00d4ff;"></div><span>Procesos automatizados</span></div>
        <div class="legend-item"><div class="color-box" style="background:#003566;"></div><span>Procesos manuales</span></div>
      </div>
      <p class="example-note">*Ejemplo de visualización del avance de automatización.</p>
    </section>

    <section id="objetivos" data-aos="fade-left">
      <h2>Objetivos del Proyecto</h2>
      <ul>
        <li>Automatizar la generación de estados financieros.</li>
        <li>Integrar indicadores financieros clave para análisis estratégico.</li>
        <li>Reducir tiempo operativo en más de 80%.</li>
        <li>Disminuir errores manuales y mejorar precisión.</li>
        <li>Capacitar al equipo PEI en herramientas tecnológicas avanzadas.</li>
      </ul>
    </section>

    <section id="resultados" data-aos="fade-right">
      <h2>Resultados Clave</h2>
      <canvas id="chartResultados"></canvas>
      <div class="legend">
        <div class="legend-item"><div class="color-box" style="background:#00d4ff;"></div><span>Tiempo</span></div>
        <div class="legend-item"><div class="color-box" style="background:#00b4d8;"></div><span>Tamaño</span></div>
        <div class="legend-item"><div class="color-box" style="background:#90e0ef;"></div><span>Ahorro</span></div>
      </div>
      <p class="example-note">*Ejemplo ilustrativo de resultados simulados para presentación.</p>
    </section>

    <section id="indicadores" data-aos="zoom-in">
      <h2>Indicadores Financieros Integrados</h2>
      <canvas id="chartIndicadores"></canvas>
      <div class="legend">
        <div class="legend-item"><div class="color-box" style="background:#00d4ff;"></div><span>Liquidez</span></div>
        <div class="legend-item"><div class="color-box" style="background:#00b4d8;"></div><span>Rentabilidad</span></div>
        <div class="legend-item"><div class="color-box" style="background:#0077b6;"></div><span>Endeudamiento</span></div>
        <div class="legend-item"><div class="color-box" style="background:#90e0ef;"></div><span>Margen</span></div>
        <div class="legend-item"><div class="color-box" style="background:#48cae4;"></div><span>Rotación</span></div>
      </div>
      <p class="example-note">*Ejemplo de radar financiero con datos simulados.</p>
    </section>

    <section id="impacto" data-aos="fade-up">
      <h2>Impacto y Alcance</h2>
      <canvas id="chartImpacto"></canvas>
      <div class="legend">
        <div class="legend-item"><div class="color-box" style="background:#00d4ff;"></div><span>Eficiencia</span></div>
        <div class="legend-item"><div class="color-box" style="background:#ff6f61;"></div><span>Innovación</span></div>
      </div>
      <p class="example-note">*Ejemplo ilustrativo de impacto progresivo del proyecto.</p>
    </section>

    <section id="kanban" data-aos="fade-up">
      <h2>Gestión de Proyecto (Kanban)</h2>
      <div class="kanban">
        <div class="kanban-column">
          <h3>Pendiente</h3>
          <div class="task">Recopilación de datos financieros</div>
          <div class="task">Identificación de indicadores PEI</div>
        </div>
        <div class="kanban-column">
          <h3>En Progreso</h3>
          <div class="task">Desarrollo de macros y Power Query</div>
          <div class="task">Integración con reportes contables</div>
        </div>
        <div class="kanban-column">
          <h3>Completado</h3>
          <div class="task">Validación de resultados</div>
          <div class="task">Presentación de resultados finales</div>
        </div>
      </div>
      <p class="example-note">*Ejemplo de implementación del método Kanban aplicado al proyecto.</p>
    </section>

    <section id="conclusiones" data-aos="fade-up">
      <h2>Conclusiones y próximos pasos</h2>
      <ul>
        <li>La automatización redujo significativamente tiempos y tamaño de archivos, mejorando la calidad y disponibilidad de la información.</li>
        <li>Se confirmaron beneficios operativos y una reducción sustancial de errores manuales en la consolidación.</li>
        <li>Se recomienda escalar la solución a otras áreas contables y evaluar integración con Power BI para cuadros ejecutivos.</li>
      </ul>
      <h3 style="color:#9aa4b2; font-size:14px; margin-top:12px;">Próximos pasos</h3>
      <ul>
        <li>Plan piloto de expansión a otra unidad durante 2 meses.</li>
        <li>Diseño de dashboards ejecutivos en Power BI (fase de trabajo: 4 semanas).</li>
        <li>Monitoreo y ajuste continuo de indicadores y reglas en Power Query.</li>
      </ul>
    </section>

    <section id="riesgos" data-aos="fade-up">
      <h2>Riesgos y mitigación</h2>
      <ul>
        <li><strong>Dependencia tecnológica:</strong> Mitigar con documentación y capacitación.</li>
        <li><strong>Calidad de datos:</strong> Validaciones automáticas y listas de chequeo.</li>
        <li><strong>Cambios en fuentes:</strong> Parametrizar conexiones y pruebas periódicas.</li>
      </ul>
      <p class="example-note">*Contenido resumido. Datos y cronograma son de ejemplo para la presentación.</p>
    </section>
  </main>

  <footer data-aos="fade-up">
    Cali, Valle del Cauca — 10 de noviembre de 2025 | Aval Fiduciaria — Área PEI.
  </footer>

  <script>
    AOS.init({duration:1000});

    new Chart(document.getElementById('chartResumen'), {
      type: 'doughnut',
      data: {labels: ['Procesos automatizados', 'Manuales'], datasets: [{data: [85, 15], backgroundColor: ['#00d4ff', '#003566']}]},
      options: {plugins:{legend:{display:false}}, animation:{duration:1500}}
    });

    new Chart(document.getElementById('chartResultados'), {
      type: 'bar',
      data: {labels: ['Tiempo', 'Tamaño', 'Ahorro'], datasets: [{label: 'Mejora', data: [83, 95, 83], backgroundColor: ['#00d4ff','#00b4d8','#90e0ef']}]},
      options:{scales:{x:{ticks:{color:'#fff'}},y:{ticks:{color:'#fff'}}}, plugins:{legend:{display:false}}, animation:{duration:1200}}
    });

    new Chart(document.getElementById('chartIndicadores'), {
      type:'radar',
      data:{labels:['Liquidez','Rentabilidad','Endeudamiento','Margen','Rotación'],datasets:[{label:'Nivel',data:[90,85,70,88,92],backgroundColor:'rgba(0,212,255,0.2)',borderColor:'#00d4ff',borderWidth:2,pointBackgroundColor:'#00d4ff'}]},
      options:{scales:{r:{grid:{color:'rgba(255,255,255,0.2)'},pointLabels:{color:'#fff'}}}, plugins:{legend:{display:false}}, animation:{duration:1200}}
    });

    new Chart(document.getElementById('chartImpacto'), {
      type:'line',
      data:{labels:['Diagnóstico','Desarrollo','Implementación','Resultados'],datasets:[
        {label:'Eficiencia',data:[20,50,80,100],borderColor:'#00d4ff',backgroundColor:'rgba(0,212,255,0.3)',fill:true,tension:0.3},
        {label:'Innovación',data:[10,30,60,90],borderColor:'#ff6f61',backgroundColor:'rgba(255,111,97,0.3)',fill:true,tension:0.3}
      ]},
      options:{scales:{x:{ticks:{color:'#fff'}},y:{ticks:{color:'#fff'}}}, plugins:{legend:{display:false}}, animation:{duration:1200}}
    });
  </script>
</body>
</html>
