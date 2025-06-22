<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Semangat Uqiii 💖</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
      background-color: #fff0f5;
      overflow-x: hidden;
      text-align: center;
    }

    .scene {
      display: none;
      padding: 40px 20px;
    }

    .active {
      display: block;
    }

    button {
      padding: 12px 24px;
      background-color: #ff69b4;
      border: none;
      color: white;
      border-radius: 10px;
      font-size: 16px;
      cursor: pointer;
      margin-top: 20px;
    }

    .effect {
      font-size: 60px;
      animation: pop 0.5s ease;
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      opacity: 0;
    }

    @keyframes pop {
      0% { transform: scale(0.5) translate(-50%, -50%); opacity: 0; }
      50% { transform: scale(1.2) translate(-50%, -50%); opacity: 1; }
      100% { transform: scale(1) translate(-50%, -50%); opacity: 0; }
    }

    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background: pink;
      transform: rotate(45deg);
      animation: float 4s linear infinite;
    }

    .heart::before,
    .heart::after {
      content: '';
      position: absolute;
      width: 20px;
      height: 20px;
      background: pink;
      border-radius: 50%;
    }

    .heart::before {
      top: -10px;
      left: 0;
    }

    .heart::after {
      left: -10px;
      top: 0;
    }

    @keyframes float {
      0% {
        bottom: 0;
        opacity: 1;
      }
      100% {
        bottom: 100%;
        opacity: 0;
      }
    }

    #audioOverlay {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: transparent;
      z-index: 9999;
    }
  </style>
</head>
<body>

<!-- Audio trigger overlay -->
<div id="audioOverlay" onclick="initAudio()"></div>

<!-- Scene 1 -->
<div class="scene active" id="scene1">
  <h1>Halooo Uqiii 👋</h1>
  <p>Aku Rayii, baru aja iseng nyoba ngoding lagi sbg lulusan multimedia dan kebetulan kepikiran kamu yang lagi belajar ujikom... 😖</p>
  <div id="effect1" class="effect">🙌</div>
  <button onclick="nextScene(2, 'effect1')">Lanjut...</button>
</div>

<!-- Scene 2 -->
<div class="scene" id="scene2">
  <p>Aku tau kamu lagi stress, kepala mungkin udah kayak ujian negara... 😵‍💫</p>
  <p>...tapi jangan panik, yuk lanjut dikit~</p>
  <div id="effect2" class="effect">🤲</div>
  <button onclick="nextScene(3, 'effect2')">Oke, aku siap!</button>
</div>

<!-- Scene 3 -->
<div class="scene" id="scene3">
  <p>SEMANGAT BABYY!!! 🥺💖</p>
  <p>Rayii dukung kamu dari pojokan dengan power sayang dan file rar berisi cinta, anjayy 😤</p>
  <div id="effect3" class="effect">🫶</div>
  <button onclick="nextScene(4, 'effect3'); startLove();">Masih pengen dimotivasi 😭</button>
</div>

<!-- Scene 4 -->
<div class="scene" id="scene4">
  <h2>Apapun hasilnya nanti...</h2>
  <p>Rayii tetep bangga sama kamu 😭</p>
  <p>Kamu udah berjuang segitu kerasnya 🫶</p>
  <h3>Kamu hebat, Uqiii... semangattttttttt! 💗</h3>
  <img src="uqirayii.jpg.png" width="250" style="margin-top: 20px; border-radius: 20px;">
</div>

<audio id="bgAudio" preload="auto" loop>
  <source src="kamu.mp3 (1).mp3" type="audio/mpeg">
  Browser kamu tidak mendukung pemutar audio.
</audio>

<script>
  const audio = document.getElementById("bgAudio");
  const overlay = document.getElementById("audioOverlay");

  function initAudio() {
    audio.load();
    audio.play().then(() => {
      overlay.style.display = 'none';
    }).catch(() => {
      alert("Klik dulu biar musiknya jalan yaa 💖");
    });
  }

  function nextScene(num, effectId) {
    const scenes = document.querySelectorAll('.scene');
    scenes.forEach(scene => scene.classList.remove('active'));
    document.getElementById('scene' + num).classList.add('active');
    if (effectId) {
      const effect = document.getElementById(effectId);
      effect.style.opacity = '1';
      effect.style.animation = 'pop 0.5s ease';
      setTimeout(() => {
        effect.style.animation = '';
        effect.style.opacity = '0';
      }, 1000);
    }
  }

  function startLove() {
    for (let i = 0; i < 50; i++) {
      let heart = document.createElement('div');
      heart.classList.add('heart');
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 5000);
    }
  }
</script>

</body>
</html>
