<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />
<title>Sevgilim Olur Musun? 💖</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    height: 100vh;
    overflow: hidden;
    background: radial-gradient(ellipse at center, #0b0033 0%, #140034 70%, #1e1048 100%);
    font-family: 'Pacifico', cursive;
    color: #fff;
    user-select: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  .stars {
    position: fixed;
    width: 100vw;
    height: 100vh;
    top: 0; left: 0;
    background: transparent;
    pointer-events: none;
    z-index: 0;
  }
  .stars::before, .stars::after {
    content: "";
    position: absolute;
    width: 200%;
    height: 200%;
    top: -50%;
    left: -50%;
    background-repeat: repeat;
    background-image: radial-gradient(white 1px, transparent 2px);
    animation: twinkle 5s linear infinite;
  }
  .stars::after {
    animation-delay: 2.5s;
    opacity: 0.5;
  }
  @keyframes twinkle {
    0%, 100% {background-position: 0 0;}
    50% {background-position: 100px 100px;}
  }

  .cloud {
    position: fixed;
    top: 15vh;
    width: 220px;
    height: 120px;
    background: rgba(255,255,255,0.15);
    border-radius: 100px;
    filter: blur(12px);
    animation: cloudMove linear infinite;
    z-index: 1;
  }
  .cloud:nth-child(1) {
    left: -250px;
    animation-duration: 90s;
    top: 10vh;
  }
  .cloud:nth-child(2) {
    left: -300px;
    animation-duration: 110s;
    top: 25vh;
  }
  .cloud:nth-child(3) {
    left: -220px;
    animation-duration: 100s;
    top: 18vh;
  }
  @keyframes cloudMove {
    0% {transform: translateX(0);}
    100% {transform: translateX(150vw);}
  }

  h1 {
    font-size: 4.2rem;
    margin: 0;
    z-index: 10;
    text-shadow: 0 0 20px #ff6f91, 0 0 40px #ff6f91, 0 0 60px #ff6f91;
    user-select: none;
  }

  #buttons {
    margin-top: 60px;
    position: relative;
    width: 360px;
    height: 170px;
    z-index: 20;
  }

  button {
    position: absolute;
    padding: 18px 42px;
    font-size: 22px;
    border-radius: 50px;
    border: none;
    cursor: pointer;
    user-select: none;
    box-shadow: 0 10px 20px rgba(0,0,0,0.3);
    transition: transform 0.2s ease, box-shadow 0.3s ease;
    touch-action: manipulation;
    font-weight: 700;
  }
  button:focus {
    outline: none;
  }

  #yesBtn {
    background: linear-gradient(45deg, #ff6f91, #ff9671);
    color: #fff;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    box-shadow: 0 0 40px #ff6f91;
    z-index: 22;
    filter: drop-shadow(0 0 15px #ff6f91);
  }
  #yesBtn:hover {
    box-shadow: 0 0 60px #ff6f91, 0 0 100px #ff9671;
    transform: translate(-50%, -50%) scale(1.15);
  }

  #noBtn {
    background: linear-gradient(45deg, #845ec2, #d65db1);
    color: #fff;
    top: 20px;
    left: 20px;
    box-shadow: 0 0 30px #845ec2;
    animation: pulse 2s infinite;
    z-index: 23;
  }
  @keyframes pulse {
    0%, 100% {
      transform: scale(1);
      box-shadow: 0 0 25px #845ec2;
    }
    50% {
      transform: scale(1.1);
      box-shadow: 0 0 45px #d65db1;
    }
  }

  #message {
    margin-top: 50px;
    font-size: 28px;
    text-align: center;
    min-height: 160px;
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.8s ease, transform 0.8s ease;
    text-shadow: 0 0 20px #ff6f91;
    user-select: none;
    white-space: pre-line;
    line-height: 1.5;
    z-index: 30;
  }
  #message.show {
    opacity: 1;
    transform: translateY(0);
  }

  #message span {
    opacity: 0;
    display: block;
    animation-fill-mode: forwards;
    animation-name: fadeInLine;
    animation-duration: 1.2s;
    animation-timing-function: ease-in-out;
    animation-delay: var(--delay);
    line-height: 1.6;
  }

  @keyframes fadeInLine {
    to {
      opacity: 1;
    }
  }

  #message .heart-emoji {
    font-size: 2.4rem;
    animation: heartBeat 1.5s ease-in-out infinite;
    display: inline-block;
    margin-left: 6px;
    vertical-align: middle;
  }

  @keyframes heartBeat {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.3); }
  }

  .heart {
    position: fixed;
    width: 50px;
    height: 50px;
    background: #ff6f91;
    transform: rotate(-45deg);
    animation: flyUp 1.7s forwards ease-out;
    z-index: 9999;
    pointer-events: none;
    filter: drop-shadow(0 0 10px #ff6f91);
  }
  .heart::before,
  .heart::after {
    content: "";
    position: absolute;
    width: 50px;
    height: 50px;
    background: #ff6f91;
    border-radius: 50%;
  }
  .heart::before {
    top: -25px;
    left: 0;
  }
  .heart::after {
    left: 25px;
    top: 0;
  }
  @keyframes flyUp {
    0% {
      opacity: 1;
      transform: translateY(0) scale(1) rotate(-45deg);
    }
    100% {
      opacity: 0;
      transform: translateY(-250px) scale(1.7) rotate(-45deg);
    }
  }

  #counter {
    margin-top: 28px;
    font-size: 20px;
    color: #ffb3c6;
    text-shadow: 0 0 12px #d65db1;
    user-select: none;
    z-index: 25;
  }

  #restartBtn {
    margin-top: 40px;
    padding: 14px 48px;
    font-size: 22px;
    border-radius: 50px;
    border: none;
    background: #ff6f91;
    color: white;
    cursor: pointer;
    box-shadow: 0 0 30px #ff6f91;
    display: none;
    transition: background-color 0.3s ease;
    user-select: none;
    z-index: 30;
  }
  #restartBtn:hover {
    background-color: #ff467e;
  }
  #restartBtn.shake {
    animation-name: shake;
    animation-duration: 0.5s;
    animation-iteration-count: 1;
  }

  @keyframes shake {
    0%, 100% { transform: translateX(0); }
    20%, 60% { transform: translateX(-6px); }
    40%, 80% { transform: translateX(6px); }
  }

  @keyframes glow {
    0% { box-shadow: 0 0 20px #ff6f91; }
    100% { box-shadow: 0 0 45px #ff6f91, 0 0 60px #ff9671; }
  }

  .top-right-video {
    position: fixed;
    top: 20px;
    right: 20px;
    width: 360px;
    height: 200px;
    background: rgba(0,0,0,0.35);
    padding: 10px 14px;
    box-shadow: 0 6px 20px rgba(0,0,0,0.7);
    border-radius: 16px;
    z-index: 9999;
    display: none;
    flex-direction: column;
    align-items: center;
    user-select: none;
  }
  .top-right-video h3 {
    color: #fff;
    font-size: 20px;
    margin: 0 0 8px 0;
    text-align: center;
    font-weight: 700;
    text-shadow: 0 0 10px #ff6f91;
  }
  .top-right-video iframe {
    width: 100%;
    height: calc(100% - 32px);
    border-radius: 12px;
    border: none;
    filter: drop-shadow(0 0 8px #ff6f91);
  }

  @media(max-width: 450px) {
    h1 {
      font-size: 3rem;
    }
    #buttons {
      width: 280px;
      height: 140px;
      margin-top: 40px;
    }
    #yesBtn, #noBtn {
      font-size: 18px;
      padding: 14px 32px;
    }
    .top-right-video {
      width: 280px;
      height: 160px;
      top: 12px;
      right: 12px;
      padding: 8px 10px;
    }
    .top-right-video h3 {
      font-size: 16px;
      margin-bottom: 6px;
    }
  }
</style>
</head>
<body>

<div class="stars"></div>
<div class="cloud"></div>
<div class="cloud"></div>
<div class="cloud"></div>

<h1>Sevgilim Olur Musun?</h1>

<div id="buttons" aria-label="Seçenekler">
  <button id="yesBtn" aria-label="Evet">Evet</button>
  <button id="noBtn" aria-label="Hayır">Hayır</button>
</div>

<div id="message" role="alert" aria-live="polite"></div>
<div id="counter" aria-live="polite">Hayır butonundan kaçış sayısı: 0</div>
<button id="restartBtn" aria-label="Yeniden Oyna">Yeniden Oyna</button>

<div id="videoContainer" class="top-right-video" aria-label="Romantik şarkı videosu">
  <h3>Benden Sana Gelsin</h3>
  <iframe
    id="ytPlayer"
    src="https://www.youtube.com/embed/i6lXqifn5CU?rel=0&autoplay=1&mute=0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    title="Benden Sana Gelsin"
  ></iframe>
</div>

<script>
  const noBtn = document.getElementById('noBtn');
  const yesBtn = document.getElementById('yesBtn');
  const container = document.getElementById('buttons');
  const message = document.getElementById('message');
  const counterEl = document.getElementById('counter');
  const restartBtn = document.getElementById('restartBtn');
  const videoContainer = document.getElementById('videoContainer');
  const ytPlayer = document.getElementById('ytPlayer');

  const containerWidth = container.clientWidth;
  const containerHeight = container.clientHeight;
  const btnWidth = noBtn.offsetWidth;
  const btnHeight = noBtn.offsetHeight;

  let escapeCount = 0;
  let gameOver = false;

  const soundEscape = new Audio('https://actions.google.com/sounds/v1/cartoon/wood_plank_flicks.ogg');
  const soundClick = new Audio('https://actions.google.com/sounds/v1/cartoon/clang_and_wobble.ogg');
  const soundHeart = new Audio('https://actions.google.com/sounds/v1/alarms/heart_beat_loop.ogg');

  soundEscape.volume = 0.3;
  soundClick.volume = 0.3;
  soundHeart.volume = 0.3;

  let posX = 20;
  let posY = 20;
  noBtn.style.left = posX + 'px';
  noBtn.style.top = posY + 'px';

  function moveNoBtnTowardsCursor(clientX, clientY) {
    if(gameOver) return;

    const rect = container.getBoundingClientRect();
    const mouseX = clientX - rect.left;
    const mouseY = clientY - rect.top;

    const btnCenterX = posX + btnWidth / 2;
    const btnCenterY = posY + btnHeight / 2;

    const distX = mouseX - btnCenterX;
    const distY = mouseY - btnCenterY;
    const distance = Math.hypot(distX, distY);

    const safeDistance = 130;

    if(distance < safeDistance) {
      let moveX = btnCenterX - mouseX;
      let moveY = btnCenterY - mouseY;

      const length = Math.hypot(moveX, moveY);
      moveX /= length;
      moveY /= length;

      const speed = (safeDistance - distance) / safeDistance * 27 + 10;

      posX += moveX * speed;
      posY += moveY * speed;

      posX = Math.min(Math.max(0, posX), containerWidth - btnWidth);
      posY = Math.min(Math.max(0, posY), containerHeight - btnHeight);

      noBtn.style.left = posX + 'px';
      noBtn.style.top = posY + 'px';

      noBtn.style.animation = 'pulse 0.4s';
      setTimeout(() => {
        noBtn.style.animation = 'pulse 2s infinite';
      }, 400);

      escapeCount++;
      counterEl.textContent = `Hayır butonundan kaçış sayısı: ${escapeCount}`;
      soundEscape.currentTime = 0;
      soundEscape.play();
    }
  }

  container.addEventListener('mousemove', (e) => {
    moveNoBtnTowardsCursor(e.clientX, e.clientY);
  });

  container.addEventListener('touchmove', (e) => {
    const touch = e.touches[0];
    moveNoBtnTowardsCursor(touch.clientX, touch.clientY);
  });

  const poemLines = [
    "Seni sevdim,",
    "Seni birdenbire değil usul usul sevdim.",
    "‘Uyandım bir sabah’ gibi değil,",
    "Öyle değil nasıl yürür özsu dal uçlarına",
    "Ve gün ışığı sislerden düşsel ovalara…",
    "Seni sevdim…",
    "Artık tek mümkünüm sensin…"
  ];

  function showPoemAnimated() {
    message.innerHTML = "";
    poemLines.forEach((line, index) => {
      const span = document.createElement('span');
      span.textContent = line;
      span.style.setProperty('--delay', `${index * 1.3}s`);
      message.appendChild(span);

      if (index === poemLines.length - 2) {
        // Kalp emojisi ekle
        const heartEmoji = document.createElement('span');
        heartEmoji.textContent = "❤️";
        heartEmoji.classList.add('heart-emoji');
        span.appendChild(heartEmoji);
      }
    });
    message.classList.add('show');
  }

  // Ambient müzik (çok hafif ses, loop)
  const ambientAudio = new Audio('https://cdn.pixabay.com/download/audio/2022/03/20/audio_bdfc64db19.mp3?filename=relaxing-ambient-11274.mp3');
  ambientAudio.loop = true;
  ambientAudio.volume = 0.15;

  yesBtn.addEventListener('click', () => {
    if(gameOver) return;

    gameOver = true;
    showPoemAnimated();
    restartBtn.style.display = 'inline-block';
    counterEl.style.color = '#ff6f91';

    soundClick.currentTime = 0;
    soundClick.play();

    soundHeart.currentTime = 0;
    soundHeart.play();

    ambientAudio.currentTime = 0;
    ambientAudio.play();

    // Buton parlama animasyonu
    yesBtn.style.animation = "glow 2s infinite alternate";
    
    for(let i=0; i<25; i++) {
      createHeart();
    }

    videoContainer.style.display = 'flex';
  });

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart');

    const colors = ['#ff6f91', '#ff9671', '#f2a365'];
    heart.style.backgroundColor = colors[Math.floor(Math.random()*colors.length)];
    heart.style.left = (Math.random() * window.innerWidth) + 'px';
    heart.style.top = (window.innerHeight - 80) + 'px';
    document.body.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 1700);
  }

  restartBtn.addEventListener('click', () => {
    gameOver = false;
    escapeCount = 0;
    counterEl.textContent = `Hayır butonundan kaçış sayısı: 0`;
    counterEl.style.color = '#ffb3c6';
    message.textContent = '';
    message.classList.remove('show');
    restartBtn.style.display = 'none';

    posX = 20;
    posY = 20;
    noBtn.style.left = posX + 'px';
    noBtn.style.top = posY + 'px';

    videoContainer.style.display = 'none';

    ytPlayer.src = ytPlayer.src;

    ambientAudio.pause();
    ambientAudio.currentTime = 0;
    
    yesBtn.style.animation = "";
    
    // Restart butonu shake animasyonu
    restartBtn.classList.add('shake');
    setTimeout(() => {
      restartBtn.classList.remove('shake');
    }, 500);
  });
</script>

</body>
</html>
