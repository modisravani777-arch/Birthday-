<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Happy Birthday 🎉</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee);
      background-size: 400% 400%;
      animation: gradient 15s ease infinite;
      overflow: hidden;
      font-family: 'Comic Sans MS', cursive, sans-serif;
    }
    @keyframes gradient {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    h1 {
      font-size: 60px;
      color: white;
      text-shadow: 0 0 10px #ff6ec4, 0 0 20px #ff6ec4, 0 0 30px #ff6ec4;
      animation: glow 2s ease-in-out infinite alternate;
    }
    @keyframes glow {
      from { text-shadow: 0 0 10px #ff6ec4, 0 0 20px #ff6ec4; }
      to { text-shadow: 0 0 20px #ff6ec4, 0 0 40px #ff6ec4; }
    }
    .cake {
      font-size: 100px;
      margin: 20px 0;
    }
    .message {
      font-size: 24px;
      color: white;
      margin-top: 10px;
    }
    .balloon {
      position: absolute;
      bottom: -150px;
      width: 60px;
      height: 80px;
      background: red;
      border-radius: 50%;
      animation: rise 10s infinite ease-in;
    }
    .balloon:before {
      content: '';
      position: absolute;
      width: 2px;
      height: 100px;
      background: white;
      top: 80px;
      left: 50%;
      transform: translateX(-50%);
    }
    @keyframes rise {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(-120vh) scale(0.8); opacity: 0; }
    }
    canvas {
      position: absolute;
      top: 0;
      left: 0;
      pointer-events: none;
    }
  </style>
</head>
<body>
  <h1>🎉 Happy Birthday My Friend 🎉</h1>
  <div class="cake">🎂</div>
  <p class="message">Wishing you endless happiness, love & success 💖</p>

  <!-- Balloons -->
  <div class="balloon" style="left: 10%; background: #ff6b6b; animation-delay: 0s;"></div>
  <div class="balloon" style="left: 30%; background: #6bc5ff; animation-delay: 2s;"></div>
  <div class="balloon" style="left: 50%; background: #ffd93d; animation-delay: 4s;"></div>
  <div class="balloon" style="left: 70%; background: #9d6bff; animation-delay: 6s;"></div>
  <div class="balloon" style="left: 90%; background: #4cd137; animation-delay: 8s;"></div>

  <!-- Confetti Canvas -->
  <canvas id="confetti"></canvas>

  <script>
    // Confetti Effect
    const canvas = document.getElementById("confetti");
    const ctx = canvas.getContext("2d");
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const confetti = [];
    for (let i = 0; i < 200; i++) {
      confetti.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        r: Math.random() * 6 + 4,
        d: Math.random() * 100,
        color: "hsl(" + Math.random() * 360 + ",100%,50%)",
        tilt: Math.floor(Math.random() * 10) - 10
      });
    }

    function draw() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      confetti.forEach((c) => {
        ctx.beginPath();
        ctx.fillStyle = c.color;
        ctx.fillRect(c.x, c.y, c.r, c.r);
      });
      update();
    }

    function update() {
      confetti.forEach((c) => {
        c.y += Math.cos(c.d) + 1 + c.r / 2;
        c.x += Math.sin(c.d);
        if (c.y > canvas.height) {
          c.x = Math.random() * canvas.width;
          c.y = -10;
        }
      });
    }

    setInterval(draw, 20);
    window.addEventListener("resize", () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    });
  </script>
</body>
</html>
