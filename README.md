<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Capital que Crece</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,500;0,9..144,600;1,9..144,500;1,9..144,600&family=Manrope:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --cream:#FBF3ED;
    --blush:#F4D9DC;
    --blush-soft:#F8E5E3;
    --ink:#2A2620;
    --forest:#203524;
    --forest-deep:#152219;
    --wine:#7C2438;
    --pill-green:#DCE7B4;
    --pill-pink:#F3C9D6;
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--cream);
    color:var(--ink);
    font-family:'Manrope', sans-serif;
    line-height:1.6;
  }
  h1,h2,h3,.serif{font-family:'Fraunces', serif; font-weight:500;}
  em{font-style:italic; font-weight:500;}
  a{color:inherit; text-decoration:none;}
  img,video{max-width:100%; display:block;}
  .wrap{max-width:1120px; margin:0 auto; padding:0 32px;}
  @media (max-width:640px){ .wrap{padding:0 20px;} }

  /* NAV */
  header{
    position:sticky; top:0; z-index:50;
    background:rgba(251,243,237,0.92);
    backdrop-filter:blur(6px);
    border-bottom:1px solid var(--blush);
  }
  nav{display:flex; align-items:center; justify-content:space-between; padding:18px 0;}
  .brand{font-size:1.25rem; font-weight:500; letter-spacing:0.02em; color:var(--forest); font-family:'Fraunces',serif;}
  .brand em{color:var(--wine);}
  .navlinks{display:flex; gap:36px; font-size:0.95rem; font-weight:600;}
  .navlinks a{border-bottom:1px solid transparent; padding-bottom:2px; transition:border-color .2s;}
  .navlinks a:hover{border-color:var(--wine);}

  /* HERO */
  .hero{
    padding:100px 0 70px; text-align:center; position:relative; overflow:hidden;
  }
  .hero::before{
    content:""; position:absolute; top:-220px; left:50%; transform:translateX(-50%);
    width:900px; height:900px; border-radius:50%;
    background:radial-gradient(circle at 50% 40%, var(--blush-soft), var(--blush) 70%, transparent 72%);
    opacity:0.6; z-index:0;
  }
  .hero .inner{position:relative; z-index:1;}
  .eyebrow{
    text-transform:uppercase; letter-spacing:0.08em; font-size:0.8rem;
    font-weight:700; color:var(--wine); margin-bottom:16px;
  }
  .hero h1{font-size:clamp(2.3rem, 4.6vw, 3.6rem); color:var(--forest); max-width:780px; margin:0 auto 18px;}
  .hero p.lead{font-size:1.1rem; max-width:560px; margin:0 auto; color:#5a5647;}

  .paths{
    display:grid; grid-template-columns:1fr 1px 1fr;
    max-width:920px; margin:64px auto 0; position:relative; z-index:1;
    border:1px solid var(--blush); background:#fff;
    border-radius:24px; overflow:hidden;
  }
  .paths .divider{background:var(--blush);}
  .path{padding:48px 40px; text-align:left;}
  .path .kicker{font-size:0.8rem; color:var(--wine); font-weight:700; text-transform:uppercase; letter-spacing:0.06em; margin-bottom:10px;}
  .path h2{font-size:1.6rem; color:var(--forest); margin-bottom:14px;}
  .path p{font-size:0.98rem; color:#5a5647; margin-bottom:26px;}
  .btn{
    display:inline-block; padding:14px 30px; font-size:0.95rem; font-weight:700;
    border-radius:999px; transition:transform .15s, opacity .2s;
  }
  .btn:hover{opacity:0.88; transform:translateY(-1px);}
  .btn-green{background:var(--pill-green); color:var(--forest-deep);}
  .btn-pink{background:var(--pill-pink); color:var(--wine);}
  @media (max-width:720px){
    .paths{grid-template-columns:1fr; }
    .paths .divider{height:1px; width:100%;}
  }

  /* SECTIONS */
  section.block{padding:88px 0; border-top:1px solid var(--blush);}
  .block .tag{font-size:0.8rem; font-weight:700; color:var(--wine); text-transform:uppercase; letter-spacing:0.06em; margin-bottom:10px;}
  .block h2{font-size:clamp(1.8rem,3vw,2.4rem); color:var(--forest); max-width:600px; margin-bottom:20px;}
  .block .intro{max-width:600px; color:#5a5647; margin-bottom:40px;}

  .video-frame{
    background:var(--forest); color:var(--blush-soft);
    aspect-ratio:16/9; max-width:760px; border-radius:16px;
    display:flex; align-items:center; justify-content:center;
    font-size:0.95rem; margin-bottom:48px;
  }

  .offer-list{display:grid; grid-template-columns:repeat(3,1fr); gap:28px; margin-bottom:48px;}
  .offer-list div{border-top:2px solid var(--wine); padding-top:14px;}
  .offer-list h3{font-size:1.05rem; font-weight:700; color:var(--forest); margin-bottom:8px; font-family:'Fraunces',serif;}
  .offer-list p{font-size:0.92rem; color:#5a5647;}
  @media (max-width:720px){ .offer-list{grid-template-columns:1fr;} }

  .testimonials{margin-top:56px;}
  .testimonials h3.serif{font-size:1.3rem; color:var(--forest); margin-bottom:24px;}
  .test-grid{display:grid; grid-template-columns:repeat(3,1fr); gap:24px;}
  @media (max-width:900px){ .test-grid{grid-template-columns:1fr 1fr;} }
  @media (max-width:640px){ .test-grid{grid-template-columns:1fr;} }
  .test-card{background:#fff; border:1px solid var(--blush); padding:22px; border-radius:16px;}
  .test-card.video{aspect-ratio:9/16; display:flex; align-items:center; justify-content:center; color:var(--wine); font-size:0.85rem; text-align:center; background:var(--blush-soft);}
  .test-card p{font-size:0.92rem; color:#5a5647; font-style:italic; margin-bottom:12px;}
  .test-card .name{font-size:0.85rem; font-weight:700; color:var(--forest); font-style:normal;}

  /* COMUNIDAD */
  #comunidad{background:var(--forest); color:var(--cream);}
  #comunidad .tag{color:var(--pill-green);}
  #comunidad h2{color:var(--cream);}
  #comunidad .intro{color:#cfd8c4;}

  footer{padding:48px 0; text-align:center; font-size:0.85rem; color:#8a8672;}
</style>
</head>
<body>

<header>
  <nav class="wrap">
    <div class="brand">Capital que <em>Crece</em></div>
    <div class="navlinks">
      <a href="#inicio">Inicio</a>
      <a href="#trade">Trade with us</a>
      <a href="#partner">Partner with us</a>
      <a href="#comunidad">Comunidad</a>
    </div>
  </nav>
</header>

<section class="hero" id="inicio">
  <div class="wrap inner">
    <div class="eyebrow">Bróker regulado · Acompañamiento real</div>
    <h1>Escoge tu <em>camino</em></h1>
    <p class="lead">Dos formas de construir capital con nosotros: operando en el mercado o creciendo como socio de negocio.</p>

    <div class="paths">
      <div class="path">
        <div class="kicker">Para traders</div>
        <h2>Trade with <em>us</em></h2>
        <p>Copytrading, señales y análisis de mercado, acompañado por alguien que opera desde dentro del bróker, no desde afuera.</p>
        <a href="#trade" class="btn btn-green">Ver cómo empezar</a>
      </div>
      <div class="divider"></div>
      <div class="path">
        <div class="kicker">Para socios</div>
        <h2>Partner with <em>us</em></h2>
        <p>Conviértete en IB y genera ingresos recurrentes recomendando el bróker, con acompañamiento directo en todo el proceso.</p>
        <a href="#partner" class="btn btn-pink">Ver la oportunidad</a>
      </div>
    </div>
  </div>
</section>

<section class="block" id="trade">
  <div class="wrap">
    <div class="tag">Trade with us</div>
    <h2>Opera con acompañamiento real, no con <em>promesas</em></h2>
    <p class="intro">Un recorrido corto de cómo funciona el copytrading, las señales y el análisis que recibes al operar con nosotros.</p>

    <div class="video-frame">[ Video de introducción — Trade with us ]</div>

    <div class="offer-list">
      <div>
        <h3>Copytrading manual</h3>
        <p>Replica operaciones reales, explicadas paso a paso, sin depender de un robot que nadie entiende.</p>
      </div>
      <div>
        <h3>Señales</h3>
        <p>Entradas y salidas claras, con el contexto de mercado detrás de cada una.</p>
      </div>
      <div>
        <h3>Análisis de mercado</h3>
        <p>Lectura semanal de los activos que más movemos, para que entiendas el porqué, no solo el qué.</p>
      </div>
    </div>

    <a href="https://puvip.co/la-partners/Y0mUZMsv" class="btn btn-green">Abrir cuenta y empezar</a>

    <div class="testimonials">
      <h3 class="serif">Lo que dicen quienes ya operan con nosotros</h3>
      <div class="test-grid">
        <div class="test-card video">[ Testimonio en video ]</div>
        <div class="test-card">
          <p>"Reemplaza con una cita real de un cliente sobre su experiencia con el copytrading o las señales."</p>
          <div class="name">— Nombre, país</div>
        </div>
        <div class="test-card">
          <p>"Segunda cita real: qué cambió en su forma de operar desde que empezó."</p>
          <div class="name">— Nombre, país</div>
        </div>
      </div>
    </div>
  </div>
</section>

<section class="block" id="partner">
  <div class="wrap">
    <div class="tag">Partner with us</div>
    <h2>Genera ingresos recomendando lo que ya <em>usas</em></h2>
    <p class="intro">Cómo funciona el programa de IB, qué acompañamiento recibes y qué necesitas para empezar.</p>

    <div class="video-frame">[ Video de introducción — Partner with us ]</div>

    <div class="offer-list">
      <div>
        <h3>Comisión recurrente</h3>
        <p>Ingresos por cada cliente que refieras y siga operando, sin techo definido.</p>
      </div>
      <div>
        <h3>Material listo para compartir</h3>
        <p>Contenido, plantillas y recursos para que no empieces desde cero.</p>
      </div>
      <div>
        <h3>Acompañamiento directo</h3>
        <p>Soporte personal en cada paso del proceso de afiliación y crecimiento.</p>
      </div>
    </div>

    <a href="#" class="btn btn-pink">Agendar una llamada</a>

    <div class="testimonials">
      <h3 class="serif">Historias de socios actuales</h3>
      <div class="test-grid">
        <div class="test-card video">[ Testimonio en video ]</div>
        <div class="test-card">
          <p>"Reemplaza con una cita real de un IB sobre cómo empezó y qué resultado ha tenido."</p>
          <div class="name">— Nombre, país</div>
        </div>
        <div class="test-card">
          <p>"Segunda cita real de otro socio."</p>
          <div class="name">— Nombre, país</div>
        </div>
      </div>
    </div>
  </div>
</section>

<section class="block" id="comunidad">
  <div class="wrap">
    <div class="tag">Comunidad</div>
    <h2>Un espacio para seguir <em>aprendiendo</em>, más allá de trading o partnership</h2>
    <p class="intro">Educación financiera desde cero, con rutas para quienes quieren construir patrimonio de distintas formas — no solo operando en el mercado.</p>
    <a href="#" class="btn btn-green">Conocer la comunidad en Skool</a>
  </div>
</section>

<footer>
  <div class="wrap">© Capital que Crece — Todos los derechos reservados</div>
</footer>

</body>
</html>
