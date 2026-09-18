<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday!</title>
  
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
  
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Caveat:wght@600&family=Poppins:wght@300;400;600&family=Playfair+Display:ital@1&display=swap');

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
    }

    body {
      background: linear-gradient(135deg, #0b091a, #1a0c27, #2d112c);
      min-height: 100vh;
      color: #fff;
      overflow-x: hidden;
      position: relative;
    }

    #bg-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      pointer-events: none;
      z-index: 1;
    }

    .container {
      position: relative;
      z-index: 10;
      max-width: 800px;
      margin: 0 auto;
      padding: 20px;
      text-align: center;
    }

    .glass-card {
      background: rgba(255, 255, 255, 0.05);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid rgba(255, 255, 255, 0.12);
      border-radius: 28px;
      padding: 35px 20px;
      margin-bottom: 30px;
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.4);
    }

    h1, h2 {
      color: #ffb7c5;
      letter-spacing: 0.5px;
      margin-bottom: 15px;
    }

    .handwritten {
      font-family: 'Caveat', cursive;
      font-size: 2.5rem;
      color: #ffd1dc;
    }

    .btn {
      background: linear-gradient(45deg, #ff4d6d, #ff758f);
      color: white;
      border: none;
      padding: 14px 32px;
      font-size: 1rem;
      border-radius: 50px;
      cursor: pointer;
      box-shadow: 0 4px 20px rgba(255, 77, 109, 0.5);
      transition: all 0.3s ease;
      margin-top: 15px;
    }

    .btn:hover {
      transform: translateY(-2px) scale(1.04);
      box-shadow: 0 6px 25px rgba(255, 77, 109, 0.7);
    }

    .hidden { display: none !important; }

    .beating-heart {
      font-size: 80px;
      animation: beat 1.2s infinite ease-in-out;
      margin: 20px 0;
    }

    @keyframes beat {
      0%, 100% { transform: scale(1); filter: drop-shadow(0 0 10px #ff4d6d); }
      50% { transform: scale(1.25); filter: drop-shadow(0 0 25px #ff758f); }
    }

    #timer {
      font-size: 1.5rem;
      font-weight: 600;
      color: #ffb703;
      letter-spacing: 2px;
      margin-top: 15px;
    }

    .tree-container {
      position: relative;
      width: 100%;
      height: 380px;
      margin: 20px 0;
    }

    .heart-frame {
      position: absolute;
      width: 80px;
      height: 80px;
      cursor: pointer;
      transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      z-index: 20;
    }

    .heart-frame:hover {
      transform: scale(1.25) rotate(5deg) !important;
      filter: drop-shadow(0 0 15px #ff4d6d);
    }

    .heart-frame img {
      width: 100%;
      height: 100%;
      clip-path: path('M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z');
      object-fit: cover;
      background: #ff758f;
    }

    .balloon-box {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin: 25px 0;
    }

    .balloon {
      width: 65px;
      height: 80px;
      background: linear-gradient(135deg, #ff4d6d, #ff758f);
      border-radius: 50% 50% 50% 50% / 40% 40% 60% 60%;
      cursor: pointer;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 24px;
      box-shadow: inset -5px -5px 12px rgba(0,0,0,0.3);
      transition: transform 0.3s ease;
    }

    .cake {
      width: 170px;
      height: 95px;
      background: linear-gradient(to bottom, #f72585, #b5179e);
      margin: 40px auto 20px;
      border-radius: 14px 14px 0 0;
      position: relative;
      box-shadow: inset 0 14px 0 #4cc9f0;
    }

    .candles {
      display: flex;
      justify-content: space-evenly;
      position: absolute;
      top: -25px;
      width: 100%;
    }

    .candle {
      width: 10px;
      height: 25px;
      background: #fff;
      border-radius: 3px;
      position: relative;
    }

    .flame {
      width: 12px;
      height: 16px;
      background: #ffb703;
      border-radius: 50% 50% 20% 20%;
      position: absolute;
      top: -16px;
      left: -1px;
      cursor: pointer;
      box-shadow: 0 0 15px #ffb703;
    }

    .swiper {
      width: 100%;
      padding: 20px 0 40px;
    }

    .swiper-slide {
      background: rgba(255, 255, 255, 0.95);
      padding: 12px 12px 20px 12px;
      border-radius: 16px;
      color: #333;
      box-shadow: 0 12px 30px rgba(0,0,0,0.5);
    }

    .swiper-slide img {
      width: 100%;
      height: 240px;
      object-fit: cover;
      border-radius: 10px;
    }

    .modal {
      position: fixed;
      top: 0; left: 0; width: 100vw; height: 100vh;
      background: rgba(0,0,0,0.85);
      backdrop-filter: blur(12px);
      display: flex; justify-content: center; align-items: center;
      z-index: 10000;
    }

    .modal-content {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(25px);
      border: 1px solid rgba(255, 255, 255, 0.2);
      border-radius: 24px;
      padding: 30px;
      max-width: 480px;
      width: 90%;
      text-align: center;
      color: #fff;
      max-height: 85vh;
      overflow-y: auto;
    }

    .modal-content p {
      line-height: 1.7;
      font-size: 0.95rem;
      color: #f0e6ef;
      margin: 15px 0;
      text-align: left;
    }

    .img-modal img {
      max-width: 85%;
      max-height: 70vh;
      border-radius: 16px;
      border: 3px solid #ff758f;
    }
  </style>
</head>
<body>

  <audio id="bg-music" src="song.mp3" loop></audio>
  <canvas id="bg-canvas"></canvas>

  <div class="container">

    <div id="countdown-screen" class="glass-card">
      <div class="beating-heart">💖</div>
      <h2>Counting Down To November 8, 2026 ✨</h2>
      <p style="color:#d8e2dc;">Something truly special is blooming for you...</p>
      <div id="timer">00d : 00h : 00m : 00s</div>
    </div>

    <div id="main-flow" class="hidden">
      <div id="intro-card" class="glass-card">
        <h1 class="handwritten">Happy Birthday Gauri ✨</h1>
        <p style="color:#e0e1dd; margin-bottom:20px;">A tiny universe filled with sweet memories...</p>
        <button class="btn" onclick="openSurprise()">Open Surprise 💖</button>
      </div>

      <div id="surprise-content" class="hidden">
        <div class="glass-card">
          <h1 class="handwritten" style="font-size: 3rem;">Happy Birthday Tanya! 🎉</h1>
          <p style="color:#f2e9e4;">You make the world softer and brighter just by being in it ✨</p>
        </div>

        <div class="glass-card">
          <h2>Tree of Love Memories 🌳✨</h2>
          <p style="font-size:0.85rem; color:#ffb7c5; margin-bottom:10px;">(Tap any heart frame to view photo!)</p>
          <div class="tree-container">
            <canvas id="tree-canvas" width="360" height="340"></canvas>
            <div class="heart-frame" style="top: 45px; left: 10%;" onclick="expandImage('photo1.jpg')"><img src="photo1.jpg" onerror="this.src='https://picsum.photos/200/200?random=1'"></div>
            <div class="heart-frame" style="top: 20px; left: 42%;" onclick="expandImage('photo2.jpg')"><img src="photo2.jpg" onerror="this.src='https://picsum.photos/200/200?random=2'"></div>
            <div class="heart-frame" style="top: 60px; right: 10%;" onclick="expandImage('photo3.jpg')"><img src="photo3.jpg" onerror="this.src='https://picsum.photos/200/200?random=3'"></div>
          </div>
        </div>

        <div class="glass-card">
          <h2>Pop the Balloons! 🎈</h2>
          <p id="balloon-text" style="color:#f2e9e4;">Tap each balloon to reveal wishes!</p>
          <div class="balloon-box">
            <div class="balloon" onclick="popBalloon(this, 'Always Smile 😊')">🎈</div>
            <div class="balloon" style="background:#7209b7;" onclick="popBalloon(this, 'Stay Blessed 🌟')">🎈</div>
            <div class="balloon" style="background:#4cc9f0;" onclick="popBalloon(this, 'Keep Glowing 💖')">🎈</div>
          </div>
        </div>

        <div class="glass-card">
          <h2>Make a Wish & Blow Candles 🎂</h2>
          <p id="cake-text" style="color:#f2e9e4;">Tap all flames to blow them out!</p>
          <div class="cake">
            <div class="candles">
              <div class="candle"><div class="flame" onclick="blowCandle(this)"></div></div>
              <div class="candle"><div class="flame" onclick="blowCandle(this)"></div></div>
              <div class="candle"><div class="flame" onclick="blowCandle(this)"></div></div>
            </div>
          </div>
        </div>

        <div class="glass-card">
          <h2>For the moments we keep returning to ✨</h2>
          <div class="swiper mySwiper">
            <div class="swiper-wrapper">
              <div class="swiper-slide"><img src="photo1.jpg" onerror="this.src='https://picsum.photos/400/300?random=1'"></div>
              <div class="swiper-slide"><img src="photo2.jpg" onerror="this.src='https://picsum.photos/400/300?random=2'"></div>
              <div class="swiper-slide"><img src="photo3.jpg" onerror="this.src='https://picsum.photos/400/300?random=3'"></div>
            </div>
          </div>
          <button class="btn" onclick="openNote()">Read Secret Letter 💌</button>
        </div>
      </div>
    </div>
  </div>

  <div id="note-modal" class="modal hidden">
    <div class="modal-content">
      <h2 class="handwritten" style="font-size: 2.8rem; text-align:center;">To My Favourite Person 💌</h2>
      <p>Happy Birthday Tanya! ✨</p>
      <p>I honestly never knew how to express these feelings out loud to you, but today feels like the right time. You are genuinely my first and last best friend—my male and female best friend, all wrapped into one single amazing person. You hold a place in my life that nobody else ever could.</p>
      <p>There are tiny little details that constantly remind me of you. Every time I hear that word <i>"rizz"</i> from our old conversations, a random smile instantly pops up on my face. And whenever the song <i>"Maula Mere Maula"</i> plays, my mind automatically drifts straight back to memories of you. You have no idea how much I genuinely adore you and admire the person you are.</p>
      <p>Right now, I am completely locked into my JEE preparation, focusing with everything I've got. But the moment my JEE gets completed, I'm going to reach back out and talk to you properly just like before.</p>
      <p>Until then, stay happy, stay glowing, and keep shining bright. You deserve all the joy in this world.</p>
      <p style="text-align:right; font-family:'Caveat', cursive; font-size:1.6rem; color:#ffb7c5; margin-top:20px;">Always here for you ❤️</p>
      <button class="btn" style="width:100%; margin-top:10px;" onclick="closeNote()">Close Letter 💖</button>
    </div>
  </div>

  <div id="img-modal" class="modal img-modal hidden" onclick="closeImage()"><img id="modal-img" src="" alt="Enlarged Memory"></div>

  <script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
  <script>
    const targetDate = new Date('November 8, 2026 00:00:00').getTime();
    function updateCountdown() {
      const diff = targetDate - new Date().getTime();
      if (diff <= 0) {
        document.getElementById('countdown-screen').classList.add('hidden');
        document.getElementById('main-flow').classList.remove('hidden');
      } else {
        const days = Math.floor(diff / (1000 * 60 * 60 * 24));
        const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((diff % (1000 * 60)) / 1000);
        document.getElementById('timer').innerText = `${days}d : ${hours}h : ${minutes}m : ${seconds}s`;
      }
    }
    setInterval(updateCountdown, 1000); updateCountdown();
    function openSurprise() { document.getElementById('bg-music').play().catch(() => {}); document.getElementById('intro-card').classList.add('hidden'); document.getElementById('surprise-content').classList.remove('hidden'); drawRealisticTree(); initSwiper(); }
    function popBalloon(el, text) { el.style.transform = 'scale(0)'; el.style.pointerEvents = 'none'; document.getElementById('balloon-text').innerText = text; }
    let candlesBlown = 0;
    function blowCandle(flame) { flame.style.display = 'none'; candlesBlown++; if (candlesBlown === 3) document.getElementById('cake-text').innerText = 'Happy Birthday Tanya! 🎉 ✨'; }
    function openNote() { document.getElementById('note-modal').classList.remove('hidden'); }
    function closeNote() { document.getElementById('note-modal').classList.add('hidden'); }
    function expandImage(src) { document.getElementById('modal-img').src = src; document.getElementById('img-modal').classList.remove('hidden'); }
    function closeImage() { document.getElementById('img-modal').classList.add('hidden'); }
    function drawRealisticTree() {
      const canvas = document.getElementById('tree-canvas'); const ctx = canvas.getContext('2d'); ctx.clearRect(0, 0, canvas.width, canvas.height);
      const trunkGradient = ctx.createLinearGradient(180, 340, 180, 160); trunkGradient.addColorStop(0, '#3a1c29'); trunkGradient.addColorStop(1, '#6b2d45');
      ctx.strokeStyle = trunkGradient; ctx.lineWidth = 8; ctx.lineCap = 'round'; ctx.beginPath(); ctx.moveTo(180, 340); ctx.quadraticCurveTo(175, 250, 180, 170); ctx.stroke();
      ctx.lineWidth = 4; ctx.beginPath(); ctx.moveTo(178, 230); ctx.quadraticCurveTo(120, 190, 80, 140); ctx.moveTo(179, 210); ctx.quadraticCurveTo(240, 170, 280, 130); ctx.moveTo(180, 180); ctx.quadraticCurveTo(150, 140, 130, 100); ctx.stroke();
      for (let i = 0; i < 65; i++) setTimeout(() => { const x = 180 + (Math.random() - 0.5) * 260; const y = 130 + (Math.random() - 0.5) * 150; const size = Math.random() * 8 + 12; ctx.fillStyle = `hsl(${Math.random() * 35 + 325}, 90%, ${Math.random() * 20 + 65}%)`; ctx.font = `${size}px serif`; ctx.fillText('💖', x, y); }, i * 20);
    }
    function initSwiper() { new Swiper('.mySwiper', { effect: 'cards', grabCursor: true }); }
  </script>
</body>
</html>
