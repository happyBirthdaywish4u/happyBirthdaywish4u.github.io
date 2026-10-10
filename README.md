<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday Misba ! 🌸🩵</title>
  
  <!-- EXTERNAL LIBRARIES (Tailwind CSS, Canvas Confetti, Fonts) -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;700;800&family=Dancing+Script:wght@700&family=Caveat:wght@600&display=swap" rel="stylesheet">

  <style>
    body {
      font-family: 'Outfit', sans-serif;
      background: radial-gradient(circle at center, #1e1b4b 0%, #0f172a 60%, #030712 100%);
      color: #f8fafc;
      overflow-x: hidden;
      min-height: 100vh;
    }

    .font-handwriting { font-family: 'Dancing Script', cursive; }
    .font-note { font-family: 'Caveat', cursive; }

    /* 3D Falling Petals Canvas Background */
    #petalCanvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      pointer-events: none;
      z-index: 1;
    }

    /* Ambient Background Glows */
    .glow-bg-pink {
      position: fixed;
      top: 10%;
      left: 15%;
      width: 350px;
      height: 350px;
      background: rgba(236, 72, 153, 0.15);
      filter: blur(120px);
      border-radius: 50%;
      pointer-events: none;
      z-index: 0;
    }
    .glow-bg-blue {
      position: fixed;
      bottom: 20%;
      right: 15%;
      width: 400px;
      height: 400px;
      background: rgba(56, 189, 248, 0.15);
      filter: blur(140px);
      border-radius: 50%;
      pointer-events: none;
      z-index: 0;
    }

    /* Floral Corner Ornaments (Upper Right & Lower Left Only) */
    .corner-floral {
      position: fixed;
      width: 220px;
      height: 220px;
      pointer-events: none;
      z-index: 2;
      opacity: 0.9;
      filter: drop-shadow(0 0 12px rgba(236, 72, 153, 0.6));
      animation: floralPulse 4s ease-in-out infinite alternate;
    }
    .top-right { top: -10px; right: -10px; }
    .bottom-left { bottom: -10px; left: -10px; transform: scale(-1); }

    @keyframes floralPulse {
      0% { opacity: 0.8; filter: drop-shadow(0 0 10px rgba(236, 72, 153, 0.5)); }
      100% { opacity: 1; filter: drop-shadow(0 0 20px rgba(56, 189, 248, 0.8)); }
    }

    /* Glassmorphism Cards */
    .glass-card {
      background: rgba(15, 23, 42, 0.65);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border: 1px solid rgba(236, 72, 153, 0.25);
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5), inset 0 0 15px rgba(56, 189, 248, 0.1);
    }

    /* Hanging Balloons Section */
    .balloon-container {
      display: flex;
      justify-content: space-around;
      width: 100%;
      position: absolute;
      top: 0;
      left: 0;
      z-index: 10;
      pointer-events: none;
    }
    .balloon {
      width: 42px;
      height: 54px;
      border-radius: 50% 50% 50% 50% / 40% 40% 60% 60%;
      position: relative;
      animation: swing 3.5s ease-in-out infinite alternate;
      cursor: pointer;
      pointer-events: auto;
      box-shadow: inset -5px -5px 10px rgba(0,0,0,0.3);
      transition: transform 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }
    .balloon::before {
      content: "";
      position: absolute;
      bottom: -12px;
      left: 50%;
      transform: translateX(-50%);
      width: 2px;
      height: 60px;
      background: rgba(255, 255, 255, 0.25);
    }
    .balloon:hover { transform: scale(1.15) translateY(-5px); }

    @keyframes swing {
      0% { transform: rotate(-5deg) translateY(0); }
      100% { transform: rotate(5deg) translateY(8px); }
    }

    /* 3D Cake Visuals & Split Cut Animation */
    .cake-container {
      position: relative;
      width: 280px;
      height: 250px;
      margin: 0 auto;
      cursor: pointer;
    }
    .cake-topper {
      position: absolute;
      top: -35px;
      left: 50%;
      transform: translateX(-50%);
      background: linear-gradient(135deg, #f472b6, #ec4899);
      color: #ffffff;
      padding: 6px 16px;
      border-radius: 20px;
      font-size: 0.85rem;
      font-weight: 800;
      letter-spacing: 0.5px;
      white-space: nowrap;
      box-shadow: 0 0 20px rgba(236, 72, 153, 0.8), 0 4px 10px rgba(0,0,0,0.5);
      border: 2px solid #ffffff;
      z-index: 25;
      animation: topperGlow 2s infinite alternate;
    }
    @keyframes topperGlow {
      0% { transform: translateX(-50%) scale(1); box-shadow: 0 0 15px rgba(236, 72, 153, 0.6); }
      100% { transform: translateX(-50%) scale(1.05); box-shadow: 0 0 25px rgba(56, 189, 248, 0.9); }
    }

    .cake-layer {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      border-radius: 16px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.4);
      transition: all 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
    }
    .layer-bottom {
      width: 220px;
      height: 75px;
      bottom: 10px;
      background: linear-gradient(135deg, #ec4899, #be185d);
      border-bottom: 8px solid #f472b6;
    }
    .layer-middle {
      width: 165px;
      height: 65px;
      bottom: 80px;
      background: linear-gradient(135deg, #38bdf8, #0284c7);
      border-bottom: 8px solid #7dd3fc;
    }
    .layer-top {
      width: 115px;
      height: 55px;
      bottom: 140px;
      background: linear-gradient(135deg, #f472b6, #38bdf8);
      border-bottom: 6px solid #ffffff;
    }

    /* Split Cake States */
    .cake-container.sliced .layer-bottom {
      transform: translateX(-50%) translateY(10px);
      clip-path: polygon(0 0, 48% 0, 48% 100%, 0 100%);
      filter: drop-shadow(-10px 10px 15px rgba(236,72,153,0.5));
    }
    .cake-container.sliced .layer-bottom::after {
      content: '';
      position: absolute;
      right: -120px;
      top: 0;
      width: 220px;
      height: 75px;
      background: linear-gradient(135deg, #ec4899, #be185d);
      border-radius: 16px;
      transform: translateX(30px);
      clip-path: polygon(52% 0, 100% 0, 100% 100%, 52% 100%);
      box-shadow: 10px 10px 15px rgba(56,189,248,0.5);
    }

    .cake-container.sliced .layer-middle {
      transform: translateX(-50%) translateY(5px);
      clip-path: polygon(0 0, 47% 0, 47% 100%, 0 100%);
    }
    .cake-container.sliced .layer-middle::after {
      content: '';
      position: absolute;
      right: -95px;
      top: 0;
      width: 165px;
      height: 65px;
      background: linear-gradient(135deg, #38bdf8, #0284c7);
      border-radius: 16px;
      transform: translateX(25px);
      clip-path: polygon(53% 0, 100% 0, 100% 100%, 53% 100%);
    }

    .cake-container.sliced .layer-top {
      transform: translateX(-50%);
      clip-path: polygon(0 0, 45% 0, 45% 100%, 0 100%);
    }
    .cake-container.sliced .layer-top::after {
      content: '';
      position: absolute;
      right: -70px;
      top: 0;
      width: 115px;
      height: 55px;
      background: linear-gradient(135deg, #f472b6, #38bdf8);
      border-radius: 16px;
      transform: translateX(20px);
      clip-path: polygon(55% 0, 100% 0, 100% 100%, 55% 100%);
    }

    /* Hidden Glowing Heart inside Sliced Cake */
    .hidden-heart {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) scale(0);
      font-size: 3rem;
      color: #f43f5e;
      filter: drop-shadow(0 0 20px #f43f5e);
      z-index: 15;
      transition: transform 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275) 0.3s;
    }
    .cake-container.sliced .hidden-heart {
      transform: translate(-50%, -50%) scale(1.3);
      animation: heartPulse 1.5s infinite alternate;
    }
    @keyframes heartPulse {
      0% { transform: translate(-50%, -50%) scale(1.2); filter: drop-shadow(0 0 15px #f43f5e); }
      100% { transform: translate(-50%, -50%) scale(1.4); filter: drop-shadow(0 0 30px #38bdf8); }
    }

    .frosting-dot {
      position: absolute;
      width: 12px;
      height: 12px;
      background: #ffffff;
      border-radius: 50%;
      box-shadow: 0 2px 4px rgba(0,0,0,0.2);
    }

    /* Candle & Flame with Smoke Animation */
    .candle {
      position: absolute;
      width: 10px;
      height: 38px;
      background: repeating-linear-gradient(45deg, #f43f5e, #f43f5e 5px, #ffffff 5px, #ffffff 10px);
      bottom: 195px;
      border-radius: 4px;
      cursor: pointer;
      z-index: 20;
    }
    .candle-1 { left: 105px; }
    .candle-2 { left: 135px; }
    .candle-3 { left: 165px; }

    .flame {
      position: absolute;
      top: -16px;
      left: 50%;
      transform: translateX(-50%);
      width: 12px;
      height: 18px;
      background: radial-gradient(ellipse at bottom, #fef08a 0%, #f97316 60%, transparent 100%);
      border-radius: 50% 50% 20% 20%;
      box-shadow: 0 0 15px #f97316, 0 0 25px #fef08a;
      animation: flicker 0.6s infinite alternate;
      transition: all 0.4s ease;
    }
    @keyframes flicker {
      0% { transform: translateX(-50%) scale(1) rotate(-2deg); }
      100% { transform: translateX(-50%) scale(1.15) rotate(2deg); }
    }

    /* Smoke animation when blown out */
    .smoke {
      position: absolute;
      top: -25px;
      left: 50%;
      transform: translateX(-50%);
      width: 8px;
      height: 8px;
      background: rgba(255, 255, 255, 0.7);
      border-radius: 50%;
      filter: blur(4px);
      opacity: 0;
      pointer-events: none;
    }
    .smoked .smoke {
      animation: riseSmoke 1.2s forwards;
    }
    @keyframes riseSmoke {
      0% { transform: translateX(-50%) translateY(0) scale(1); opacity: 0.8; }
      100% { transform: translateX(-50%) translateY(-35px) scale(2.5); opacity: 0; }
    }

    /* Knife Slice Animation */
    .knife {
      position: absolute;
      right: -30px;
      top: 30px;
      font-size: 3.2rem;
      transform: rotate(-45deg);
      transition: all 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
      opacity: 0;
      pointer-events: none;
      z-index: 30;
    }
    .knife.active {
      opacity: 1;
      pointer-events: auto;
      animation: guideCut 1.8s infinite alternate;
    }
    @keyframes guideCut {
      0% { transform: translate(0, 0) rotate(-45deg); }
      100% { transform: translate(-45px, 45px) rotate(-15deg); }
    }

    /* Polaroid Image Cards */
    .polaroid-card {
      background: #ffffff;
      padding: 12px 12px 28px 12px;
      border-radius: 6px;
      box-shadow: 0 15px 35px rgba(0,0,0,0.4);
      transition: all 0.3s ease;
      cursor: pointer;
    }
    .polaroid-card:hover {
      transform: translateY(-8px) scale(1.03) rotate(0deg) !important;
      box-shadow: 0 25px 50px rgba(236, 72, 153, 0.3);
      z-index: 20;
    }

    .pink-glow-text {
      text-shadow: 0 0 15px rgba(236, 72, 153, 0.6), 0 0 30px rgba(56, 189, 248, 0.4);
    }
  </style>
</head>
<body class="relative min-h-screen text-slate-100 flex flex-col justify-between items-center px-4 py-8">

  <!-- Ambient Glow Backgrounds -->
  <div class="glow-bg-pink"></div>
  <div class="glow-bg-blue"></div>

  <!-- 3D Falling Rose Petals Canvas -->
  <canvas id="petalCanvas"></canvas>

  <!-- ========================================================= -->
  <!-- 🌸 FLORAL VINE CORNER SVGs (Upper Right & Lower Left Only) -->
  <!-- ========================================================= -->
  
  <!-- Upper Right Corner Floral SVG -->
  <svg class="corner-floral top-right" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <linearGradient id="floralPinkBlue" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#ec4899" />
        <stop offset="50%" stop-color="#f472b6" />
        <stop offset="100%" stop-color="#38bdf8" />
      </linearGradient>
      <linearGradient id="petalFillGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="rgba(236, 72, 153, 0.25)" />
        <stop offset="100%" stop-color="rgba(56, 189, 248, 0.25)" />
      </linearGradient>
    </defs>

    <path d="M 10,20 C 30,10 80,15 110,40 C 140,65 155,100 160,180" stroke="url(#floralPinkBlue)" stroke-width="3" stroke-linecap="round"/>
    <path d="M 20,10 C 15,30 35,70 70,95 C 105,120 145,130 180,135" stroke="url(#floralPinkBlue)" stroke-width="2.5" stroke-linecap="round"/>
    <path d="M 20,20 C 10,10 5,30 25,35 C 45,40 30,15 15,25" stroke="url(#floralPinkBlue)" stroke-width="2"/>
    <path d="M 60,85 C 45,100 40,120 55,125 C 70,130 75,105 60,95" stroke="url(#floralPinkBlue)" stroke-width="2"/>
    <path d="M 140,135 C 150,150 165,160 175,150 C 185,140 160,125 145,140" stroke="url(#floralPinkBlue)" stroke-width="2"/>

    <!-- Large Central Flower -->
    <g transform="translate(120, 70)">
      <path d="M 0,0 C -25,-40 -5,-65 20,-50 C 45,-35 25,-10 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 20,-50 55,-35 50,-5 C 45,25 15,15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 35,-10 50,25 25,45 C 0,65 -15,30 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -10,35 -40,40 -50,15 C -60,-10 -25,-15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -45,0 -50,-35 -25,-45 C 0,-55 10,-20 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <circle cx="0" cy="0" r="6" fill="#38bdf8"/>
      <line x1="0" y1="0" x2="-8" y2="-20" stroke="#ec4899" stroke-width="1.5"/>
      <line x1="0" y1="0" x2="12" y2="-18" stroke="#ec4899" stroke-width="1.5"/>
      <line x1="0" y1="0" x2="18" y2="8" stroke="#ec4899" stroke-width="1.5"/>
      <line x1="0" y1="0" x2="-12" y2="15" stroke="#ec4899" stroke-width="1.5"/>
      <line x1="0" y1="0" x2="-18" y2="-10" stroke="#ec4899" stroke-width="1.5"/>
    </g>

    <!-- Smaller Flowers -->
    <g transform="translate(50, 35) scale(0.65)">
      <path d="M 0,0 C -25,-40 -5,-65 20,-50 C 45,-35 25,-10 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 20,-50 55,-35 50,-5 C 45,25 15,15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 35,-10 50,25 25,45 C 0,65 -15,30 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -10,35 -40,40 -50,15 C -60,-10 -25,-15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -45,0 -50,-35 -25,-45 C 0,-55 10,-20 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <circle cx="0" cy="0" r="5" fill="#f472b6"/>
    </g>
    <g transform="translate(140, 130) scale(0.65)">
      <path d="M 0,0 C -25,-40 -5,-65 20,-50 C 45,-35 25,-10 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 20,-50 55,-35 50,-5 C 45,25 15,15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 35,-10 50,25 25,45 C 0,65 -15,30 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -10,35 -40,40 -50,15 C -60,-10 -25,-15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -45,0 -50,-35 -25,-45 C 0,-55 10,-20 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <circle cx="0" cy="0" r="5" fill="#38bdf8"/>
    </g>
  </svg>

  <!-- Lower Left Corner Floral SVG -->
  <svg class="corner-floral bottom-left" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M 10,20 C 30,10 80,15 110,40 C 140,65 155,100 160,180" stroke="url(#floralPinkBlue)" stroke-width="3" stroke-linecap="round"/>
    <path d="M 20,10 C 15,30 35,70 70,95 C 105,120 145,130 180,135" stroke="url(#floralPinkBlue)" stroke-width="2.5" stroke-linecap="round"/>
    <path d="M 20,20 C 10,10 5,30 25,35 C 45,40 30,15 15,25" stroke="url(#floralPinkBlue)" stroke-width="2"/>
    <path d="M 60,85 C 45,100 40,120 55,125 C 70,130 75,105 60,95" stroke="url(#floralPinkBlue)" stroke-width="2"/>
    <path d="M 140,135 C 150,150 165,160 175,150 C 185,140 160,125 145,140" stroke="url(#floralPinkBlue)" stroke-width="2"/>
    <g transform="translate(120, 70)">
      <path d="M 0,0 C -25,-40 -5,-65 20,-50 C 45,-35 25,-10 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 20,-50 55,-35 50,-5 C 45,25 15,15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 35,-10 50,25 25,45 C 0,65 -15,30 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -10,35 -40,40 -50,15 C -60,-10 -25,-15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -45,0 -50,-35 -25,-45 C 0,-55 10,-20 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <circle cx="0" cy="0" r="6" fill="#38bdf8"/>
    </g>
    <g transform="translate(50, 35) scale(0.65)">
      <path d="M 0,0 C -25,-40 -5,-65 20,-50 C 45,-35 25,-10 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 20,-50 55,-35 50,-5 C 45,25 15,15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 35,-10 50,25 25,45 C 0,65 -15,30 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -10,35 -40,40 -50,15 C -60,-10 -25,-15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -45,0 -50,-35 -25,-45 C 0,-55 10,-20 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <circle cx="0" cy="0" r="5" fill="#f472b6"/>
    </g>
    <g transform="translate(140, 130) scale(0.65)">
      <path d="M 0,0 C -25,-40 -5,-65 20,-50 C 45,-35 25,-10 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 20,-50 55,-35 50,-5 C 45,25 15,15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C 35,-10 50,25 25,45 C 0,65 -15,30 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -10,35 -40,40 -50,15 C -60,-10 -25,-15 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <path d="M 0,0 C -45,0 -50,-35 -25,-45 C 0,-55 10,-20 0,0 Z" fill="url(#petalFillGrad)" stroke="url(#floralPinkBlue)" stroke-width="2"/>
      <circle cx="0" cy="0" r="5" fill="#38bdf8"/>
    </g>
  </svg>

  <!-- Top Hanging Balloons -->
  <div class="balloon-container pt-2">
    <div class="balloon" style="background: #ec4899;" onclick="popBalloon(this)"></div>
    <div class="balloon" style="background: #38bdf8; animation-delay: -0.5s;" onclick="popBalloon(this)"></div>
    <div class="balloon" style="background: #f472b6; animation-delay: -1s;" onclick="popBalloon(this)"></div>
    <div class="balloon" style="background: #60a5fa; animation-delay: -1.5s;" onclick="popBalloon(this)"></div>
    <div class="balloon" style="background: #a855f7; animation-delay: -2s;" onclick="popBalloon(this)"></div>
    <div class="balloon" style="background: #38bdf8; animation-delay: -2.5s;" onclick="popBalloon(this)"></div>
    <div class="balloon" style="background: #ec4899; animation-delay: -3s;" onclick="popBalloon(this)"></div>
  </div>

  <!-- Header Audio Controls -->
  <div class="fixed top-4 left-4 z-50 flex items-center space-x-2">
    <button onclick="openSongModal()" class="px-3.5 py-2 rounded-full glass-card border border-pink-400/40 text-xs font-semibold tracking-wider hover:bg-pink-500/20 transition flex items-center space-x-2">
      <i class="fas fa-plus text-pink-400"></i>
      <span>CUSTOM SONG</span>
    </button>
    <button id="musicBtn" onclick="toggleAudio()" class="px-4 py-2 rounded-full glass-card border border-sky-400/40 text-xs font-semibold tracking-wider hover:bg-sky-500/20 transition flex items-center space-x-2">
      <i id="musicIcon" class="fas fa-music text-pink-400"></i>
      <span id="musicText">PLAY SONG</span>
    </button>
  </div>

  <!-- Main Content Wrapper -->
  <main class="w-full max-w-4xl z-10 space-y-16 mt-16 mb-12">

    <!-- HERO CELEBRATION SECTION -->
    <section class="text-center space-y-6">
      <div class="inline-block px-4 py-1.5 rounded-full glass-card border border-pink-500/30 text-xs font-bold uppercase tracking-widest text-pink-300 shadow-lg">
        🎉 Celebration Time !
      </div>
      
      <h1 class="text-4xl md:text-6xl font-extrabold tracking-tight pink-glow-text">
        Happy Birthday, <span class="bg-gradient-to-r from-pink-400 via-sky-300 to-blue-400 bg-clip-text text-transparent">Misba !</span>
      </h1>
      
      <p id="subInstruction" class="text-slate-300 text-sm md:text-base max-w-lg mx-auto font-light">
        Pop the balloons! Blow out the candles, and let's cut the cake together 🎂
      </p>

      <!-- 3D Interactive Cake with Topper Header -->
      <div class="py-8">
        <div class="cake-container" id="cakeContainer" onclick="handleCakeInteraction()">
          <div class="cake-topper">✨ Happy Birthday Misba! ✨</div>
          <div class="hidden-heart">💖</div>

          <!-- Candles with Smoke effect -->
          <div class="candle candle-1" id="candle1"><div class="flame" id="flame1"></div><div class="smoke"></div></div>
          <div class="candle candle-2" id="candle2"><div class="flame" id="flame2"></div><div class="smoke"></div></div>
          <div class="candle candle-3" id="candle3"><div class="flame" id="flame3"></div><div class="smoke"></div></div>

          <!-- Cake Tiers -->
          <div class="cake-layer layer-top">
            <div class="frosting-dot" style="left: 10px; top: -6px;"></div>
            <div class="frosting-dot" style="left: 50px; top: -6px;"></div>
            <div class="frosting-dot" style="right: 10px; top: -6px;"></div>
          </div>
          <div class="cake-layer layer-middle">
            <div class="frosting-dot" style="left: 15px; top: -6px;"></div>
            <div class="frosting-dot" style="left: 75px; top: -6px;"></div>
            <div class="frosting-dot" style="right: 15px; top: -6px;"></div>
          </div>
          <div class="cake-layer layer-bottom">
            <div class="frosting-dot" style="left: 20px; top: -6px;"></div>
            <div class="frosting-dot" style="left: 105px; top: -6px;"></div>
            <div class="frosting-dot" style="right: 20px; top: -6px;"></div>
          </div>

          <div class="knife" id="knife">🔪</div>
        </div>
      </div>

      <div class="flex justify-center items-center space-x-4">
        <button id="actionBtn" onclick="handleActionButton()" class="px-8 py-3.5 rounded-full font-bold text-sm tracking-wider uppercase transition-all duration-300 transform hover:scale-105 shadow-lg bg-gradient-to-r from-pink-500 to-sky-500 hover:from-pink-600 hover:to-sky-600 text-white shadow-pink-500/25">
          🔥 Blow Out Candles
        </button>
      </div>
    </section>

    <!-- POLAROID SNAPSHOTS -->
    <section class="space-y-6">
      <div class="text-center">
        <span class="text-xs font-bold uppercase tracking-widest text-sky-400">Polaroid Snapshots</span>
        <h2 class="text-2xl md:text-3xl font-bold mt-1">Snapshots</h2>
      </div>

      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 md:gap-6 pt-2">
        <div class="polaroid-card -rotate-3" onclick="openLightbox('Misbapic.jpeg')">
          <img src="Misbapic.jpeg" alt="Snapshot 1" class="w-full h-48 object-cover rounded">
          <p class="font-note text-center text-slate-800 text-xl mt-3 font-semibold">Good Vibes ✨</p>
        </div>
        <div class="polaroid-card rotate-2" onclick="openLightbox('misbaprofile1.jpeg')">
          <img src="misbaprofile1.jpeg" alt="Snapshot 2" class="w-full h-48 object-cover rounded">
          <p class="font-note text-center text-slate-800 text-xl mt-3 font-semibold">Fun Moments 🌟</p>
        </div>
        <div class="polaroid-card -rotate-2" onclick="openLightbox('misbaprofile2.jpeg')">
          <img src="misbaprofile2.jpeg" alt="Snapshot 3" class="w-full h-48 object-cover rounded">
          <p class="font-note text-center text-slate-800 text-xl mt-3 font-semibold">Celebrations 🎉</p>
        </div>
        <div class="polaroid-card rotate-3" onclick="openLightbox('misba.profile3.jpeg')">
          <img src="misba.profile3.jpeg" alt="Snapshot 4" class="w-full h-48 object-cover rounded">
          <p class="font-note text-center text-slate-800 text-xl mt-3 font-semibold">Memories 💫</p>
        </div>
      </div>
    </section>

    <!-- TYPEWRITER WISH LETTER SECTION (LOCKED UNTIL CAKE IS CUT) -->
    <section id="wishLetterSection" class="glass-card rounded-2xl p-6 md:p-8 space-y-4 relative overflow-hidden transition-all duration-700 opacity-40 blur-[2px] pointer-events-none">
      <div class="flex items-center justify-between border-b border-slate-700/60 pb-3">
        <span id="letterHeaderTitle" class="text-xs font-bold uppercase tracking-widest text-pink-400">🔒 Special Wish Letter (Complete Cake Cutting to Unlock!)</span>
        <button onclick="restartTypewriter()" class="text-xs text-sky-400 hover:text-sky-300 transition">
          <i class="fas fa-redo-alt mr-1"></i> Replay
        </button>
      </div>

      <div class="min-h-[120px] text-base md:text-lg text-slate-200 leading-relaxed font-light">
        <span id="typewriterText"></span><span id="cursor" class="animate-pulse text-pink-400 font-bold">|</span>
      </div>

      <div class="text-right pt-2">
        <p class="font-handwriting text-2xl text-pink-300">— Ankit Yadav</p>
      </div>
    </section>

    <!-- QUICK INTERACTIVE REACTION SECTION -->
    <section class="glass-card rounded-2xl p-6 text-center space-y-4">
      <span class="text-xs font-bold uppercase tracking-widest text-sky-400">Quick Question</span>
      <h3 class="text-2xl font-bold">Did you enjoy this? 🎉</h3>
      <p class="text-xs text-slate-400">Let the sender know this brought a smile!</p>

      <div class="flex justify-center space-x-4 pt-2">
        <button onclick="handleReaction('loved')" class="px-6 py-2.5 rounded-full bg-pink-500 hover:bg-pink-600 text-white font-bold text-xs uppercase tracking-wider transition transform hover:scale-105 shadow-lg shadow-pink-500/30">
          💖 LOVED IT!
        </button>
        <button onclick="handleReaction('notyet')" class="px-6 py-2.5 rounded-full bg-slate-800 hover:bg-slate-700 text-slate-300 font-bold text-xs uppercase tracking-wider transition">
          😁 NOT YET
        </button>
      </div>
    </section>

    <!-- THANK-YOU / REPLY FORM -->
    <section class="glass-card rounded-2xl p-6 md:p-8 space-y-6">
      <div class="text-center space-y-1">
        <i class="fas fa-heart text-pink-500 text-3xl animate-bounce"></i>
        <h3 class="font-handwriting text-3xl text-pink-300">Happy Birthday!</h3>
        <p class="text-xs text-slate-400 uppercase tracking-widest">With best wishes, <strong class="text-sky-300">Ankit Yadav</strong></p>
      </div>

      <div class="space-y-3">
        <label class="block text-xs font-bold uppercase tracking-wider text-slate-300">Send a Thank-You Reply</label>
        <textarea id="replyText" rows="3" class="w-full bg-slate-900/80 border border-slate-700 rounded-xl p-3 text-sm text-slate-100 focus:outline-none focus:border-pink-500 transition" placeholder="Write your reply here..."></textarea>
        <button onclick="sendReply()" class="w-full py-3 rounded-xl bg-gradient-to-r from-sky-500 to-pink-500 hover:from-sky-600 hover:to-pink-600 text-white font-bold text-xs uppercase tracking-widest transition transform hover:scale-[1.01] shadow-lg">
          🚀 Send Message Back
        </button>
      </div>
      <div id="replyStatus" class="hidden text-center text-xs text-emerald-400 font-semibold"></div>
    </section>

  </main>

  <!-- CUSTOM SONG PICKER MODAL -->
  <div id="songModal" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
    <div class="glass-card rounded-2xl p-6 max-w-md w-full space-y-4 relative">
      <button onclick="closeSongModal()" class="absolute top-4 right-4 text-slate-400 hover:text-white">
        <i class="fas fa-times"></i>
      </button>
      <h3 class="text-xl font-bold text-pink-300"><i class="fas fa-music mr-2"></i>Add Your Custom Song</h3>
      <p class="text-xs text-slate-300">Upload an MP3 audio file or paste a direct audio link below:</p>

      <div class="space-y-3">
        <div>
          <label class="block text-xs text-slate-400 mb-1">Option 1: Upload File from Device</label>
          <input type="file" id="audioFileInput" accept="audio/*" onchange="handleAudioUpload(event)" class="w-full text-xs text-slate-300 file:mr-3 file:py-2 file:px-4 file:rounded-full file:border-0 file:text-xs file:font-semibold file:bg-pink-500 file:text-white hover:file:bg-pink-600 cursor-pointer">
        </div>
        <div class="text-center text-xs text-slate-500 uppercase tracking-widest">— OR —</div>
        <div>
          <label class="block text-xs text-slate-400 mb-1">Option 2: Paste Direct Audio URL (.mp3)</label>
          <input type="url" id="audioUrlInput" placeholder="https://example.com/song.mp3" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-2.5 text-xs text-slate-100 focus:outline-none focus:border-sky-400">
        </div>
        <button onclick="saveAudioUrl()" class="w-full py-2.5 rounded-xl bg-pink-500 hover:bg-pink-600 text-white font-bold text-xs uppercase tracking-wider transition">
          Set Custom Song
        </button>
      </div>
    </div>
  </div>

  <!-- LIGHTBOX MODAL -->
  <div id="lightbox" class="fixed inset-0 bg-black/90 z-50 hidden flex items-center justify-center p-4" onclick="closeLightbox()">
    <img id="lightboxImg" src="" alt="Full view" class="max-w-full max-h-[80vh] rounded-lg shadow-2xl border-2 border-pink-500/50">
  </div>

  <audio id="customAudioPlayer" src="videoplayback.weba"></audio>

  <footer class="text-center text-xs text-slate-500 py-4 z-10">
    Crafted with 🎉 for Misba | Wishes from Ankit Yadav
  </footer>

  <!-- JAVASCRIPT ENGINE -->
  <script>
    let audioContext = null;
    let isPlayingAudio = false;
    let audioTimer = null;

    function initAudio() {
      if (!audioContext) {
        audioContext = new (window.AudioContext || window.webkitAudioContext)();
      }
    }

    function playPopSound() {
      initAudio();
      const osc = audioContext.createOscillator();
      const gain = audioContext.createGain();
      osc.type = 'sine';
      osc.frequency.setValueAtTime(800, audioContext.currentTime);
      osc.frequency.exponentialRampToValueAtTime(200, audioContext.currentTime + 0.08);
      gain.gain.setValueAtTime(0.3, audioContext.currentTime);
      gain.gain.linearRampToValueAtTime(0.01, audioContext.currentTime + 0.08);
      osc.connect(gain);
      gain.connect(audioContext.destination);
      osc.start();
      osc.stop(audioContext.currentTime + 0.08);
    }

    function toggleAudio() {
      initAudio();
      const btnText = document.getElementById('musicText');
      const btnIcon = document.getElementById('musicIcon');
      const customPlayer = document.getElementById('customAudioPlayer');
      
      if (isPlayingAudio) {
        isPlayingAudio = false;
        clearInterval(audioTimer);
        if (customPlayer.src && customPlayer.src !== window.location.href) {
          customPlayer.pause();
        }
        btnText.innerText = "PLAY SONG";
        btnIcon.className = "fas fa-music text-pink-400";
      } else {
        isPlayingAudio = true;
        btnText.innerText = "PLAYING...";
        btnIcon.className = "fas fa-volume-up text-sky-400 animate-pulse";
        
        if (customPlayer.src && customPlayer.src !== window.location.href) {
          customPlayer.play().catch(() => playBirthdayMelody());
        } else {
          playBirthdayMelody();
        }
      }
    }

    function playBirthdayMelody() {
      const notes = [264, 264, 297, 264, 352, 330, 264, 264, 297, 264, 396, 352];
      let idx = 0;
      audioTimer = setInterval(() => {
        if (!isPlayingAudio) return;
        const osc = audioContext.createOscillator();
        const gain = audioContext.createGain();
        osc.frequency.setValueAtTime(notes[idx], audioContext.currentTime);
        gain.gain.setValueAtTime(0.15, audioContext.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.35);
        osc.connect(gain);
        gain.connect(audioContext.destination);
        osc.start();
        osc.stop(audioContext.currentTime + 0.35);
        idx = (idx + 1) % notes.length;
      }, 400);
    }

    function openSongModal() { document.getElementById('songModal').classList.remove('hidden'); }
    function closeSongModal() { document.getElementById('songModal').classList.add('hidden'); }

    function handleAudioUpload(e) {
      const file = e.target.files[0];
      if (file) {
        const url = URL.createObjectURL(file);
        document.getElementById('customAudioPlayer').src = url;
        alert("Custom song loaded successfully!");
        closeSongModal();
      }
    }

    function saveAudioUrl() {
      const url = document.getElementById('audioUrlInput').value.trim();
      if (url) {
        document.getElementById('customAudioPlayer').src = url;
        alert("Custom song URL set successfully!");
        closeSongModal();
      }
    }

    let candlesLit = true;
    let cakeCut = false;

    function handleActionButton() {
      if (candlesLit) {
        extinguishCandles();
      } else if (!cakeCut) {
        cutCake();
      }
    }

    function handleCakeInteraction() {
      if (candlesLit) {
        extinguishCandles();
      } else if (!cakeCut) {
        cutCake();
      }
    }

    function extinguishCandles() {
      candlesLit = false;
      document.getElementById('candle1').classList.add('smoked');
      document.getElementById('candle2').classList.add('smoked');
      document.getElementById('candle3').classList.add('smoked');

      setTimeout(() => {
        document.getElementById('flame1').style.display = 'none';
        document.getElementById('flame2').style.display = 'none';
        document.getElementById('flame3').style.display = 'none';
      }, 400);
      
      confetti({ particleCount: 60, spread: 70, origin: { y: 0.6 } });
      
      const btn = document.getElementById('actionBtn');
      btn.innerHTML = '🔪 Cut The Cake';
      btn.className = 'px-8 py-3.5 rounded-full font-bold text-sm tracking-wider uppercase transition-all duration-300 transform hover:scale-105 shadow-lg bg-gradient-to-r from-sky-400 to-blue-500 hover:from-sky-500 hover:to-blue-600 text-white shadow-sky-500/25';
      
      document.getElementById('subInstruction').innerText = 'Now click the cake or button to slice it! 🍰';
      document.getElementById('knife').classList.add('active');
    }

    function cutCake() {
      cakeCut = true;
      document.getElementById('knife').classList.remove('active');
      document.getElementById('cakeContainer').classList.add('sliced');
      
      confetti({
        particleCount: 200,
        spread: 130,
        origin: { y: 0.5 },
        colors: ['#ec4899', '#38bdf8', '#f472b6', '#60a5fa', '#ffffff']
      });

      if (!isPlayingAudio) {
        toggleAudio();
      }

      document.getElementById('subInstruction').innerText = 'Yay! Happy Birthday Misba! Wish you an incredible year ahead! 🎉';
      document.getElementById('actionBtn').style.display = 'none';

      // UNLOCK THE WISH LETTER SECTION
      const letterSec = document.getElementById('wishLetterSection');
      letterSec.classList.remove('opacity-40', 'blur-[2px]', 'pointer-events-none');
      document.getElementById('letterHeaderTitle').innerText = "✨ Special Wish Letter for Misba ✨";
      
      // Start typing animation automatically
      restartTypewriter();
    }

    function popBalloon(el) {
      playPopSound();
      el.style.transform = 'scale(1.4)';
      el.style.opacity = '0';
      setTimeout(() => el.remove(), 200);
    }

    const wishText = "Hey Misba! Wishing you a very Happy Birthday! Hope your day is filled with great moments, lots of laughter, and awesome memories. May this year bring you continuous success, joy, and everything you are working towards! Have a fantastic birthday celebration!";
    let typeIdx = 0;

    function typeWriter() {
      if (typeIdx < wishText.length) {
        document.getElementById('typewriterText').innerHTML += wishText.charAt(typeIdx);
        typeIdx++;
        setTimeout(typeWriter, 40);
      }
    }

    function restartTypewriter() {
      document.getElementById('typewriterText').innerHTML = '';
      typeIdx = 0;
      typeWriter();
    }

    function openLightbox(src) {
      document.getElementById('lightboxImg').src = src;
      document.getElementById('lightbox').classList.remove('hidden');
    }
    function closeLightbox() {
      document.getElementById('lightbox').classList.add('hidden');
    }

    function handleReaction(type) {
      if (type === 'loved') {
        confetti({ particleCount: 100, spread: 70, origin: { y: 0.7 } });
        alert("Awesome! Glad you enjoyed this birthday page! 🎉");
      } else {
        alert("Thanks for checking it out! Have a great day! 😊");
      }
    }

    function sendReply() {
      const txt = document.getElementById('replyText').value.trim();
      if (!txt) return;
      const status = document.getElementById('replyStatus');
      status.innerText = "✓ Thank you reply recorded!";
      status.classList.remove('hidden');
      document.getElementById('replyText').value = '';
    }

    /* 3D Falling Rose Petals Engine */
    const canvas = document.getElementById('petalCanvas');
    const ctx = canvas.getContext('2d');

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    class Petal {
      constructor() {
        this.reset();
      }
      reset() {
        this.x = Math.random() * canvas.width;
        this.y = -20;
        this.size = Math.random() * 12 + 8;
        this.speedY = Math.random() * 1.5 + 0.8;
        this.speedX = Math.random() * 1 - 0.5;
        this.angle = Math.random() * Math.PI * 2;
        this.spin = (Math.random() - 0.5) * 0.03;
        this.color = Math.random() > 0.5 ? '#f472b6' : '#38bdf8';
        this.opacity = Math.random() * 0.6 + 0.3;
      }
      update() {
        this.y += this.speedY;
        this.x += Math.sin(this.y / 30) + this.speedX;
        this.angle += this.spin;
        if (this.y > canvas.height + 20) this.reset();
      }
      draw() {
        ctx.save();
        ctx.translate(this.x, this.y);
        ctx.rotate(this.angle);
        ctx.globalAlpha = this.opacity;
        ctx.fillStyle = this.color;
        ctx.beginPath();
        ctx.moveTo(0, 0);
        ctx.bezierCurveTo(-this.size, -this.size / 2, -this.size, this.size, 0, this.size * 1.5);
        ctx.bezierCurveTo(this.size, this.size, this.size, -this.size / 2, 0, 0);
        ctx.fill();
        ctx.restore();
      }
    }

    const petals = Array.from({ length: 35 }, () => new Petal());

    function animatePetals() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      petals.forEach(petal => {
        petal.update();
        petal.draw();
      });
      requestAnimationFrame(animatePetals);
    }

    window.onload = () => {
      animatePetals();
    };
  </script>
</body>
</html>
