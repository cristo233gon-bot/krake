<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CiberKraken</title>

<style>
:root{
  --green:#2cff7b;
  --dark:#05060b;
  --line:#1c2747;
  --panel:#0b1020;
  --panel2:#11172b;
  --muted:#a9b2c7;
}

*{box-sizing:border-box}
body{
  margin:0;
  font-family: Arial, Helvetica, sans-serif;
  background:#05060b;
  color:white;
}

/* ===== HEADER ===== */
.topbar{
  position:fixed;
  top:0;
  width:100%;
  z-index:100;
  background:rgba(7,10,18,.75);
  backdrop-filter: blur(10px);
  border-bottom:1px solid var(--line);
}

.topbar-inner{
  max-width:1200px;
  margin:auto;
  padding:15px 20px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:16px;
}

.brand{
  display:flex;
  align-items:center;
  gap:10px;
}

.brand img{
  width:32px;
  height:32px;
  object-fit:contain;
}

.brand-name{
  font-weight:900;
  font-size:18px;
}

.brand-name span{ color:var(--green); }

.tabs{
  display:flex;
  gap:20px;
  flex-wrap:wrap;
  justify-content:flex-end;
}

.tabbtn{
  background:none;
  border:none;
  color:#aaa;
  font-weight:900;
  cursor:pointer;
  position:relative;
  padding:6px 2px;
}

.tabbtn.active,
.tabbtn:hover{
  color:var(--green);
}

.tabbtn.active:after{
  content:"";
  position:absolute;
  bottom:-6px;
  left:0;
  right:0;
  height:2px;
  background:var(--green);
  box-shadow:0 0 18px rgba(44,255,123,.25);
}

/* ===== HERO ===== */
.hero{
  position:relative;
  height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  text-align:center;
  overflow:hidden;
  padding-top:80px;
}

.bg-video{
  position:absolute;
  inset:0;
  width:100%;
  height:100%;
  object-fit:cover;
  opacity:0.5;
  z-index:0;
}

.hero:before{
  content:"";
  position:absolute;
  inset:0;
  background: radial-gradient(900px 500px at 50% 50%, rgba(0,0,0,.10), rgba(0,0,0,.72));
  z-index:1;
}

.hero-content{
  position:relative;
  z-index:2;
  padding: 0 16px;
}

.hero-logo{
  width:208px;   /* +30% (antes 160px) */
  height:208px;
  margin:auto;
  margin-bottom:25px;
  filter: drop-shadow(0 0 20px rgba(44,255,123,.18));
}

.hero-logo img{
  width:100%;
  height:100%;
  object-fit:contain;
}

.hero h1{
  font-size:80px;
  margin:0;
  font-weight:1000;
}

.hero h1 span{
  color:var(--green);
  text-shadow: 0 0 18px rgba(44,255,123,.18);
}

.hero p{
  font-size:22px;
  color:#ccc;
  margin-top:15px;
}

.cta{
  margin-top:30px;
  padding:15px 35px;
  background:var(--green);
  color:#07120b;
  border:none;
  border-radius:12px;
  font-weight:1000;
  cursor:pointer;
  box-shadow: 0 16px 50px rgba(0,0,0,.55);
}

/* ===== SECTIONS ===== */
.section{
  display:none;
  padding:120px 20px 80px;
  max-width:1200px;
  margin:auto;
}
.section.active{ display:block; }

.section-title{
  text-align:center;
  font-size:48px;
  margin: 0;
  font-weight:1000;
}
.section-title span{color:var(--green)}
.section-sub{
  text-align:center;
  max-width: 900px;
  margin: 14px auto 0;
  color: var(--muted);
  line-height:1.7;
}

/* ===== MATERIAL GRID (estilo como tu captura) ===== */
.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit, minmax(340px, 1fr));
  gap:26px;
  margin-top:40px;
}

.card{
  height:520px;
  border-radius:22px;
  overflow:hidden;
  position:relative;
  border:1px solid var(--line);
  background:
    radial-gradient(700px 340px at 30% 30%, rgba(44,255,123,.10), transparent 60%),
    radial-gradient(700px 340px at 70% 70%, rgba(100,80,255,.10), transparent 60%),
    linear-gradient(180deg, rgba(17,23,43,.85), rgba(11,16,32,.90));
  display:flex;
  flex-direction:column;
  justify-content:space-between;
  transition:.25s;
}

.card:hover{
  transform: scale(1.01);
  border-color: rgba(44,255,123,.50);
  box-shadow: 0 22px 70px rgba(0,0,0,.55);
}

.card-hero{
  height: 290px;
  display:grid;
  place-items:center;
  position:relative;
}

.card-hero img{
  width: 140px;
  height: 140px;
  object-fit:contain;
  filter: drop-shadow(0 0 18px rgba(44,255,123,.12));
  opacity:.95;
}

.card-bottom{
  padding:22px;
  background: rgba(0,0,0,.35);
  border-top:1px solid rgba(28,39,71,.65);
}

.card-bottom h3{
  margin:0;
  font-size:22px;
  font-weight:1000;
}

.card-bottom p{
  margin:10px 0 0;
  color: var(--muted);
  line-height:1.6;
  font-size:14px;
}

.btn-more{
  margin-top:18px;
  width:100%;
  padding:12px 14px;
  background: rgba(7,10,18,.25);
  border:1px solid rgba(44,255,123,.45);
  color: var(--green);
  font-weight:1000;
  border-radius:12px;
  cursor:pointer;
  transition:.15s;
}
.btn-more:hover{
  background: rgba(44,255,123,.10);
}

/* ===== MODAL ===== */
.overlay{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.65);
  display:none;
  align-items:center;
  justify-content:center;
  padding:20px;
  z-index:200;
}
.overlay.open{ display:flex; }

.modal{
  width:min(900px, 100%);
  background: linear-gradient(180deg, rgba(11,16,32,.96), rgba(7,10,18,.96));
  border:1px solid rgba(28,39,71,.9);
  border-radius:22px;
  overflow:hidden;
  box-shadow: 0 22px 90px rgba(0,0,0,.70);
}

.modal-head{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:12px;
  padding: 14px 16px;
  border-bottom:1px solid rgba(28,39,71,.65);
  background: linear-gradient(180deg, rgba(44,255,123,.10), rgba(44,255,123,.04));
}

.modal-head h4{margin:0; font-size:14px}
.close{
  border:1px solid rgba(28,39,71,.9);
  background: rgba(7,10,18,.35);
  color:white;
  padding:10px 12px;
  border-radius: 12px;
  cursor:pointer;
  font-weight:900;
}

.modal-body{
  padding: 16px;
  display:grid;
  gap: 12px;
}

.modal-top{
  display:flex;
  gap:14px;
  align-items:center;
  flex-wrap:wrap;
}
.modal-icon{
  width:76px;
  height:76px;
  border-radius: 18px;
  border:1px solid rgba(28,39,71,.8);
  background: rgba(15,21,42,.55);
  display:grid;
  place-items:center;
  overflow:hidden;
}
.modal-icon img{width:56px;height:56px;object-fit:contain}

.bullets{display:grid; gap:10px}
.bullet{
  border:1px solid rgba(28,39,71,.75);
  background: rgba(11,16,32,.55);
  border-radius: 16px;
  padding: 12px;
}
.bullet strong{display:block; font-size: 13px}
.bullet span{display:block; color: rgba(255,255,255,.70); margin-top:4px; line-height:1.6; font-size:13px}
</style>
</head>

<body>

<header class="topbar">
  <div class="topbar-inner">
    <div class="brand">
      <img src="logos/Logo pagina.png" alt="Logo">
      <div class="brand-name">Ciber<span>Kraken</span></div>
    </div>

    <nav class="tabs">
      <button class="tabbtn active" data-tab="inicio">Inicio</button>
      <button class="tabbtn" data-tab="material">Material de Estudio</button>
      <button class="tabbtn" data-tab="instalable">Instalable</button>
      <button class="tabbtn" data-tab="nosotros">Sobre Nosotros</button>
      <button class="tabbtn" data-tab="aportes">Aportes</button>
      <button class="tabbtn" data-tab="contacto">Contacto</button>
    </nav>
  </div>
</header>

<!-- INICIO -->
<section id="inicio" class="hero section active">
  <video class="bg-video" autoplay muted loop playsinline>
    <source src="media/matrix.mp4" type="video/mp4">
  </video>

  <div class="hero-content">
    <div class="hero-logo">
      <img src="logos/Logo pagina.png" alt="Logo CiberKraken">
    </div>

    <h1>Ciber<span>Kraken</span></h1>
    <p>"Formación práctica en Ciberseguridad y Seguridad TI"</p>
    <button class="cta" id="goMaterial">Explorar Material</button>
  </div>
</section>

<!-- MATERIAL -->
<section id="material" class="section">
  <h2 class="section-title">Material de <span>Estudio</span></h2>
  <p class="section-sub">
    Explora nuestra colección de recursos sobre herramientas, estándares y prácticas esenciales en ciberseguridad.
  </p>
  <div class="grid" id="materialGrid"></div>
</section>

<section id="instalable" class="section">
  <h2 class="section-title">Instalable</h2>
  <p class="section-sub">Descargas oficiales, requisitos y recomendaciones para instalar herramientas.</p>
</section>

<section id="nosotros" class="section">
  <h2 class="section-title">Sobre <span>Nosotros</span></h2>
  <p class="section-sub">CiberKraken es un blog educativo enfocado en Ciberseguridad y Seguridad TI. Fundador: Cristóbal González.</p>
</section>

<section id="aportes" class="section">
  <h2 class="section-title">Aportes</h2>
  <p class="section-sub">Plantillas, guías, checklists y material extra para la comunidad.</p>
</section>

<section id="contacto" class="section">
  <h2 class="section-title">Contacto</h2>
  <p class="section-sub">Agrega aquí correo, redes sociales o un formulario.</p>
</section>

<!-- MODAL -->
<div class="overlay" id="overlay" aria-hidden="true">
  <div class="modal" role="dialog" aria-modal="true">
    <div class="modal-head">
      <h4 id="modalTitle">Detalle</h4>
      <button class="close" id="closeBtn">Cerrar ✕</button>
    </div>
    <div class="modal-body" id="modalBody"></div>
  </div>
</div>

<script>
/* ===== Tabs ===== */
const tabs = document.querySelectorAll(".tabbtn");
const sections = document.querySelectorAll(".section");

function openTab(id){
  tabs.forEach(b=>b.classList.toggle("active", b.dataset.tab === id));
  sections.forEach(s=>s.classList.toggle("active", s.id === id));
  window.scrollTo({top:0, behavior:"smooth"});
}
tabs.forEach(btn => btn.addEventListener("click", () => openTab(btn.dataset.tab)));
document.getElementById("goMaterial").addEventListener("click", () => openTab("material"));

/* ===== Material (SIN confidencialidad / integridad / disponibilidad) ===== */
const materials = [
  {
    title:"CSIRT",
    img:"logos/csirt.png",
    short:"Equipo y procesos para responder incidentes.",
    full:[
      ["Qué es", "Un CSIRT coordina detección, contención y recuperación de incidentes."],
      ["Qué hace", "Gestión de incidentes, comunicación, análisis, lecciones aprendidas."],
      ["Por qué importa", "Reduce impacto, tiempos de respuesta y mejora la resiliencia."]
    ]
  },
  {
    title:"Estándares",
    img:"logos/estandards.png",
    short:"ISO 27001, NIST y buenas prácticas.",
    full:[
      ["ISO 27001", "Implementa un SGSI basado en riesgos y mejora continua."],
      ["NIST", "Marco: Identificar, Proteger, Detectar, Responder, Recuperar."],
      ["Uso práctico", "Ordena políticas, controles, auditorías y cumplimiento."]
    ]
  },
  {
    title:"Google Dorks",
    img:"logos/google dork.png",
    short:"Búsquedas avanzadas OSINT (uso defensivo).",
    full:[
      ["Qué es", "Operadores de búsqueda para encontrar exposición pública."],
      ["Para qué sirve", "Auditar tu propia información expuesta en internet."],
      ["Ejemplo", "Detectar archivos indexados por error (en tu propio dominio)."]
    ]
  },
  {
    title:"Kali Linux",
    img:"logos/kali.png",
    short:"Laboratorio para auditoría y pruebas de seguridad.",
    full:[
      ["Qué es", "Distribución Linux orientada a seguridad y pentesting."],
      ["Recomendación", "Usar en máquina virtual y con snapshots."],
      ["Uso correcto", "Practicar solo en entornos legales: labs/CTF/propios."]
    ]
  },
  {
    title:"Packet Tracer",
    img:"logos/packet tracer.png",
    short:"Simulación de redes Cisco para practicar.",
    full:[
      ["Qué permite", "Topologías, VLANs, routing, ACL y troubleshooting."],
      ["Para estudiar", "Segmentación, DMZ, reglas y pruebas de conectividad."],
      ["Valor", "Aprendes redes sin hardware físico."]
    ]
  },
  {
    title:"Wireshark",
    img:"logos/wireshard.png",
    short:"Análisis de tráfico para investigar y aprender protocolos.",
    full:[
      ["Qué hace", "Captura y analiza paquetes de red."],
      ["Útil para", "Detectar anomalías, investigar conexiones y DNS/HTTP/TLS."],
      ["Habilidad clave", "Filtrado y lectura de sesiones (TCP/UDP)."]
    ]
  },
  {
    title:"Snort",
    img:"logos/snort.png",
    short:"IDS/IPS basado en reglas para detectar intrusiones.",
    full:[
      ["Qué es", "Sistema de detección/prevención basado en firmas."],
      ["Qué detecta", "Escaneos, patrones, payload sospechoso."],
      ["Clave", "Afinar reglas para reducir falsos positivos."]
    ]
  },
  {
    title:"Zabbix",
    img:"logos/zabbix.png",
    short:"Monitoreo de infraestructura y alertas.",
    full:[
      ["Monitorea", "CPU, RAM, discos, servicios y disponibilidad."],
      ["Alertas", "Notificaciones por umbrales y eventos."],
      ["Uso en seguridad", "Detectar caídas, picos y comportamiento anómalo."]
    ]
  },
  {
    title:"Power BI",
    img:"logos/power bi.png",
    short:"Dashboards para indicadores y métricas de seguridad.",
    full:[
      ["Qué muestra", "Incidentes, severidad, tiempos de respuesta, tendencias."],
      ["Para qué sirve", "Tomar decisiones basadas en datos."],
      ["Ejemplo", "Panel SOC/CSIRT con métricas y evolución."]
    ]
  },
  {
    title:"Shodan",
    img:"logos/shodan.png",
    short:"Buscador de servicios expuestos (defensivo).",
    full:[
      ["Qué es", "Buscador de dispositivos/servicios expuestos en internet."],
      ["Uso correcto", "Verificar tu propia exposición (IP/dominio)." ],
      ["Detecta", "Puertos, banners, TLS, servicios mal configurados."]
    ]
  },
  {
    title:"Sitios Web",
    img:"logos/sitios web.png",
    short:"Buenas prácticas de seguridad web.",
    full:[
      ["Riesgos", "XSS, SQLi, CSRF, auth débil, malas configuraciones."],
      ["Medidas", "HTTPS, headers, validación, WAF, hardening."],
      ["Buenas prácticas", "MFA, backups, control de accesos y logs."]
    ]
  },
  {
    title:"Tipos de amenazas",
    img:"logos/tipos de amenazas.png",
    short:"Panorama de amenazas y mitigaciones.",
    full:[
      ["Amenazas", "Phishing, ransomware, malware, DDoS, fuga de datos."],
      ["Mitigación", "MFA, backups probados, hardening, monitoreo."],
      ["Clave", "Plan de respuesta a incidentes + capacitación."]
    ]
  },
  {
    title:"VMware",
    img:"logos/vmware.png",
    short:"Virtualización para laboratorios aislados.",
    full:[
      ["Para qué sirve", "Crear entornos de práctica sin riesgo."],
      ["Recomendación", "Redes NAT/Host-only y snapshots."],
      ["Ejemplo", "Kali + Windows + servidor vulnerable en lab."]
    ]
  },
  {
    title:"Visual Studio",
    img:"logos/visual.png",
    short:"Entorno de desarrollo para proyectos y aprendizaje.",
    full:[
      ["Uso", "Programación y proyectos web."],
      ["Seguridad", "Revisar dependencias, secrets y linting."],
      ["Buenas prácticas", "Git, estructura limpia y formatter."]
    ]
  }
];

/* Render Cards */
const grid = document.getElementById("materialGrid");
grid.innerHTML = materials.map((m,i)=>`
  <article class="card">
    <div class="card-hero">
      <img src="${m.img}" alt="${m.title}">
    </div>
    <div class="card-bottom">
      <h3>${m.title}</h3>
      <p>${m.short}</p>
      <button class="btn-more" data-i="${i}">Ver más</button>
    </div>
  </article>
`).join("");

/* Modal */
const overlay = document.getElementById("overlay");
const modalTitle = document.getElementById("modalTitle");
const modalBody  = document.getElementById("modalBody");
const closeBtn   = document.getElementById("closeBtn");

function openModal(item){
  modalTitle.textContent = item.title;
  modalBody.innerHTML = `
    <div class="modal-top">
      <div class="modal-icon">
        <img src="${item.img}" alt="${item.title}">
      </div>
      <div style="color: rgba(255,255,255,.75); line-height:1.6">
        ${item.short}
      </div>
    </div>
    <div class="bullets">
      ${item.full.map(b => `
        <div class="bullet">
          <strong>${b[0]}</strong>
          <span>${b[1]}</span>
        </div>
      `).join("")}
    </div>
  `;
  overlay.classList.add("open");
  overlay.setAttribute("aria-hidden","false");
}

function closeModal(){
  overlay.classList.remove("open");
  overlay.setAttribute("aria-hidden","true");
  modalBody.innerHTML = "";
}

document.addEventListener("click", (e) => {
  const btn = e.target.closest(".btn-more");
  if(btn){
    const idx = Number(btn.dataset.i);
    openModal(materials[idx]);
    return;
  }
  if(e.target === overlay) closeModal();
});

closeBtn.addEventListener("click", closeModal);
document.addEventListener("keydown", (e) => { if(e.key === "Escape") closeModal(); });
</script>

</body>
</html>
