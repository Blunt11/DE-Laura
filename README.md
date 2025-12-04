<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Servidor del Corazón ❤️</title>
  <meta name="description" content="Una pequeña web romántica — pregunta: ¿quieres ser mi novia?">
  <style>
    :root{
      --bg: #0f1724;
      --panel:#0b1220;
      --accent:#ff6b81;
      --muted:#9aa6b2;
      --glass: rgba(255,255,255,0.03);
      --card-radius:16px;
      --mono: ui-monospace, SFMono-Regular, Menlo, Monaco, "Roboto Mono", "Courier New", monospace;
    }
    *{box-sizing:border-box}
    html,body{height:100%}

    
    body{
      margin:0;
      font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background:#000;
      color:#e6f0f6;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:24px;
      position: relative;
      overflow: hidden;
    }

    /* capa 1 - fondo oscuro */
    body::before{
      content:"";
      position:fixed;
      top:0;left:0;
      width:200%;height:200%;
      background:linear-gradient(135deg,#0a0f1c 0%,#02050a 100%);
      z-index:-3;
    }

    /* capa 2 - líneas hacker animadas */
    body::after{
      content:"";
      position:fixed;
      top:-50%;left:-50%;
      width:200%;height:200%;
      background-image:
        repeating-linear-gradient(
          120deg,
          rgba(0,255,150,0.12) 0px,
          rgba(0,255,150,0.12) 2px,
          transparent 2px,
          transparent 20px
        );
      animation:hackerMove 12s linear infinite;
      opacity:0.18;
      z-index:-2;
    }

    @keyframes hackerMove{
      from{transform:translate(0,0);}
      to{transform:translate(200px,200px);}
    }

    /* ------------------------------------------
       CARD DEL CENTRO (NO MODIFICADA)
    -------------------------------------------*/
    .card{
      width:100%;
      max-width:820px;
      background: #0b1220;
      border-radius:var(--card-radius);
      padding:28px;
      box-shadow:0 10px 30px rgba(2,6,23,0.6);
      border:1px solid rgba(255,255,255,0.04);
      position:relative;
      overflow:hidden;
      z-index:10;
    }

    header{
      display:flex;
      gap:16px;
      align-items:center;
      margin-bottom:18px;
    }

    /* ------------------------------------------
       LOGO HACKER RED ALERT CON SAMY
    -------------------------------------------*/
    .logo{
      width:56px;
      height:56px;
      border-radius:12px;
      padding:0;
      background:#330000;
      border:2px solid #ff0033;
      box-shadow:0 0 14px #ff0033;
      display:flex;
      align-items:center;
      justify-content:center;
      overflow:hidden;
    }
    .logo img{
      width:100%;
      height:100%;
      object-fit:cover;
      border-radius:8px;
    }

    h1{margin:0;font-size:20px;letter-spacing:0.4px;}
    p.lead{margin:6px 0 0;color:var(--muted);font-size:14px;}

    .console{
      margin-top:16px;
      background:rgba(255,255,255,0.02);
      border-radius:12px;
      padding:18px;
      font-family:var(--mono);
      font-size:15px;
      line-height:1.5;
      color:#cfe9ff;
      min-height:160px;
      display:flex;
      flex-direction:column;
      gap:8px;
      border:1px solid rgba(255,255,255,0.02);
    }

    .line{opacity:0;transform:translateY(6px);transition:all 380ms cubic-bezier(.2,.9,.2,1);}
    .line.show{opacity:1;transform:none}

    .controls{margin-top:16px;display:flex;gap:12px;flex-wrap:wrap;}
    button{cursor:pointer;padding:12px 18px;border-radius:10px;border:0;font-weight:600;font-size:15px;box-shadow:0 6px 18px rgba(2,6,23,0.5);}
    .btn-yes{background:linear-gradient(90deg,#ff758c,#ff7eb3);color:white;}
    .btn-no{background:transparent;color:var(--muted);border:1px solid rgba(255,255,255,0.04);}
    .result{margin-top:14px;padding:14px;border-radius:10px;display:none;align-items:center;gap:12px;}
    .result.show{display:flex}
    .result-yes{background:linear-gradient(90deg,rgba(255,107,129,0.08),rgba(255,126,179,0.06));color:#ffdbe3}
    .result-no{background:rgba(255,255,255,0.02);color:var(--muted)}
    footer.small{margin-top:18px;color:var(--muted);font-size:13px}
  </style>
</head>

<body>
  <div class="card">

    <header>
      <div class="logo">
        <img src="https://scontent.fhex5-1.fna.fbcdn.net/v/t1.15752-9/593505804_1868755103755200_4550488747035639624_n.jpg?_nc_cat=108&ccb=1-7&_nc_sid=0024fc&_nc_ohc=6lEIAhRXRbgQ7kNvwHqq21b&_nc_oc=Adm1rBaz93iwkNsnn0KmCmNe67ycULle_wWBPayoV6NYoTOzOL_cm4AJZ5T14k5QZlTVX3dzIbpM2jfnzWESn8fq&_nc_ad=z-m&_nc_cid=0&_nc_zt=23&_nc_ht=scontent.fhex5-1.fna&oh=03_Q7cD4AGxnhVNgtUfdsPWge5hoxl5sIlyQL9sdcu94S4mzmdmvQ&oe=6958B393" alt="Samy">
      </div>
      <div>
        <h1>Conectando al servidor del corazón...</h1>
        <p class="lead">Un pequeño experimento romántico — abre esto y responde con sinceridad.</p>
      </div>
    </header>

    <section class="console" id="console">
      <div class="line" id="l1">Conectando al servidor del corazón...</div>
      <div class="line" id="l2">Analizando sentimientos...</div>
      <div class="line" id="l3">Comprobando historial de sonrisas...</div>
      <div class="line" id="l4">Error 404: No se encontró una razón para no quererte.</div>
      <div class="line" id="l5">¿Me darías acceso completo a tu corazón y serías mi novia?</div>
    </section>

    <div class="controls" id="controls">
      <button class="btn-yes" id="yesBtn">Sí, acepto ❤️</button>
      <button class="btn-no" id="noBtn">Necesito tiempo</button>
      <div style="margin-left:auto" class="small">Presiona una opción cuando estés lista.</div>
    </div>

    <div class="result result-yes" id="resultYes">
      <div class="status-dot" style="background:linear-gradient(90deg,#ff9aa2,#ff6b81)"></div>
      <div>
        <strong id="yesTitle">Acceso concedido ❤️</strong>
        <div class="small">Actualizando estado de relación...</div>
      </div>
    </div>

    <div class="result result-no" id="resultNo">
      <div class="status-dot"></div>
      <div>
        <strong>Calcular Nuevo intento.</strong>
        <div class="small">Aquí seguiré, con cariño y paciencia.</div>
      </div>
    </div>

    <footer class="small">
      <code>David</code> y <code>Laura</code> — Te quiero con mi alma, que esto dure toda la vida.
    </footer>
  </div>


  <script>
    const lines = [
      {id:"l1", delay:700},
      {id:"l2", delay:1500},
      {id:"l3", delay:2300},
      {id:"l4", delay:3200},
      {id:"l5", delay:3800}
    ];

    function showLines(){
      for(const l of lines){
        setTimeout(()=>{
          document.getElementById(l.id).classList.add('show');
        },l.delay);
      }
    }

    document.addEventListener("DOMContentLoaded", showLines);

    const yesBtn=document.getElementById("yesBtn");
    const noBtn=document.getElementById("noBtn");
    const resultYes=document.getElementById("resultYes");
    const resultNo=document.getElementById("resultNo");
    const consoleBox=document.getElementById("console");

    yesBtn.onclick=()=>{
      yesBtn.disabled=true; noBtn.disabled=true;
      resultYes.classList.add("show");
      setTimeout(()=>{
        const final=document.createElement("div");
        final.className="line show";
        final.textContent='David: "Prometo cuidarte, apoyarte y hacerte sonreír cada día."';
        consoleBox.appendChild(final);
      },1200);
    };

    noBtn.onclick=()=>{
      yesBtn.disabled=true; noBtn.disabled=true;
      resultNo.classList.add("show");
    };
  </script>
</body>
</html>
