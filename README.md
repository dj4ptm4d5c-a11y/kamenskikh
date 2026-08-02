# kamenskikh
сайт-визитка современного драматурга Дмитрия Каменских
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Дмитрий Каменских — драматург</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400;1,600&family=Manrope:wght@400;500;600&display=swap" rel="stylesheet">
<style>

  :root{
    --stage: #14120f;
    --curtain: #6e2a2a;
    --gold: #c9a227;
    --paper: #ede7d9;
    --stone: #8c8676;
    --hairline: rgba(237,231,217,0.14);
  }

  *{ box-sizing: border-box; }

  html{ scroll-behavior: smooth; }

  body{
    margin:0;
    background: var(--stage);
    color: var(--paper);
    font-family: 'Manrope', sans-serif;
    font-weight: 400;
    line-height: 1.7;
    position: relative;
    overflow-x: hidden;
  }

  /* --- signature: spotlight that follows the cursor over a curtain texture --- */

  #stage-texture{
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
    background-image: repeating-linear-gradient(
      90deg,
      rgba(237,231,217,0.025) 0px,
      rgba(237,231,217,0.025) 1px,
      transparent 1px,
      transparent 34px
    );
  }

  #spotlight{
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 1;
    background: radial-gradient(
      420px circle at var(--x, 50%) var(--y, 30%),
      rgba(201,162,39,0.10),
      rgba(201,162,39,0.03) 40%,
      transparent 70%
    );
    transition: background-position 0.05s linear;
  }

  @media (prefers-reduced-motion: reduce){
    #spotlight{ background: radial-gradient(600px circle at 50% 20%, rgba(201,162,39,0.09), transparent 70%); }
  }

  main{
    position: relative;
    z-index: 2;
    max-width: 680px;
    margin: 0 auto;
    padding: 14vh 24px 12vh;
  }

  /* --- hero --- */

  .eyebrow{
    font-family: 'Manrope', sans-serif;
    font-size: 12px;
    letter-spacing: 0.32em;
    text-transform: uppercase;
    color: var(--gold);
    margin: 0 0 20px;
  }

  h1{
    font-family: 'Cormorant Garamond', serif;
    font-weight: 600;
    font-size: clamp(48px, 9vw, 84px);
    line-height: 1.05;
    letter-spacing: 0.01em;
    margin: 0 0 28px;
    color: var(--paper);
  }

  .epigraph{
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: clamp(19px, 2.6vw, 23px);
    color: var(--stone);
    max-width: 46ch;
    border-left: 2px solid var(--curtain);
    padding-left: 20px;
    margin: 0 0 8px;
  }

  /* --- section rhythm --- */

  section{
    margin-top: 96px;
  }

  .section-label{
    font-family: 'Manrope', sans-serif;
    font-size: 12px;
    letter-spacing: 0.28em;
    text-transform: uppercase;
    color: var(--gold);
    margin: 0 0 28px;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .section-label::after{
    content: '';
    flex: 1;
    height: 1px;
    background: var(--hairline);
  }

  .bio p{
    font-size: 17px;
    color: var(--paper);
    max-width: 58ch;
    margin: 0 0 18px;
  }

  .bio .placeholder-note{
    font-size: 13px;
    color: var(--stone);
    font-style: italic;
  }

  /* --- works list, styled like a theatre programme --- */

  .works{
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .work{
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: baseline;
    gap: 12px 24px;
    padding: 26px 0;
    border-bottom: 1px solid var(--hairline);
  }

  .work:first-child{
    border-top: 1px solid var(--hairline);
  }

  .work-title{
    font-family: 'Cormorant Garamond', serif;
    font-weight: 600;
    font-size: 26px;
    color: var(--paper);
    margin: 0;
  }

  .work-meta{
    font-size: 13px;
    color: var(--stone);
    letter-spacing: 0.02em;
    margin: 6px 0 0;
    grid-column: 1;
  }

  .work-link{
    grid-column: 2;
    grid-row: 1 / span 2;
    align-self: center;
    font-size: 13px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--gold);
    text-decoration: none;
    border: 1px solid var(--gold);
    padding: 9px 18px;
    border-radius: 2px;
    white-space: nowrap;
    transition: background 0.2s ease, color 0.2s ease;
  }

  .work-link:hover,
  .work-link:focus-visible{
    background: var(--gold);
    color: var(--stage);
    outline: none;
  }

  /* --- footer / contact --- */

  footer{
    margin-top: 120px;
    padding-top: 32px;
    border-top: 1px solid var(--hairline);
    font-size: 13px;
    color: var(--stone);
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 12px;
  }

  footer a{
    color: var(--paper);
    text-decoration: none;
    border-bottom: 1px solid var(--hairline);
  }

  footer a:hover,
  footer a:focus-visible{
    color: var(--gold);
    border-color: var(--gold);
    outline: none;
  }

  a:focus-visible,
  button:focus-visible{
    outline: 2px solid var(--gold);
    outline-offset: 3px;
  }

  @media (max-width: 520px){
    main{ padding: 10vh 20px 10vh; }
    section{ margin-top: 72px; }
    .work{ grid-template-columns: 1fr; }
    .work-link{ grid-column: 1; grid-row: auto; justify-self: start; margin-top: 4px; }
  }

</style>
</head>
<body>

  <div id="stage-texture"></div>
  <div id="spotlight"></div>

  <main>

    <p class="eyebrow">Драматург</p>
    <h1>Дмитрий<br>Каменских</h1>
    <p class="epigraph">Здесь может быть короткая цитата или строка из пьесы — то, с чего начинается разговор со зрителем.</p>

    <section class="bio">
      <p class="section-label">О драматурге</p>
      <p>Здесь будет короткий текст о творческом пути: несколько предложений о том, чем занимается автор, в каком направлении пишет, где ставились или публиковались его пьесы.</p>
      <p class="placeholder-note">— пришлите текст, и я вставлю его сюда вместо этого места-заполнителя.</p>
    </section>

    <section class="works">
      <p class="section-label">Пьесы</p>
      <ul class="works">
        <li class="work">
          <h3 class="work-title">Название пьесы I</h3>
          <p class="work-meta">год · площадка постановки</p>
          <a class="work-link" href="#">Читать</a>
        </li>
        <li class="work">
          <h3 class="work-title">Название пьесы II</h3>
          <p class="work-meta">год · площадка постановки</p>
          <a class="work-link" href="#">Читать</a>
        </li>
        <li class="work">
          <h3 class="work-title">Название пьесы III</h3>
          <p class="work-meta">год · площадка постановки</p>
          <a class="work-link" href="#">Читать</a>
        </li>
      </ul>
    </section>

    <footer>
      <span>© Дмитрий Каменских</span>
      <a href="mailto:mail@example.com">mail@example.com</a>
    </footer>

  </main>

<script>
  const spotlight = document.getElementById('spotlight');
  const prefersReduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  if (!prefersReduced){
    window.addEventListener('mousemove', (e) => {
      spotlight.style.setProperty('--x', e.clientX + 'px');
      spotlight.style.setProperty('--y', e.clientY + 'px');
    }, { passive: true });
  }
</script>

</body>
</html>
