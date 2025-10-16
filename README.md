<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>💌 Surprise for Goomaral 💌</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(135deg, #ffb6c1, #ff69b4, #ffc0cb);
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      font-family: 'Poppins', sans-serif;
      color: white;
      text-align: center;
      overflow: hidden;
    }

    h1 {
      font-size: 2.5em;
      margin-bottom: 0.5em;
    }

    #countdown {
      font-size: 2em;
      margin-bottom: 1.5em;
    }

    button {
      background-color: white;
      color: #ff69b4;
      border: none;
      padding: 12px 30px;
      border-radius: 25px;
      font-size: 1.1em;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background-color: #ffe6f0;
    }

    #message {
      display: none;
      font-size: 1.5em;
      line-height: 1.5em;
      animation: fadeIn 2s ease;
    }

    @keyframes fadeIn {
      from {opacity: 0;}
      to {opacity: 1;}
    }

    .heart {
      position: absolute;
      color: rgba(255, 255, 255, 0.6);
      animation: float 5s linear infinite;
    }

    @keyframes float {
      from {transform: translateY(0) rotate(0);}
      to {transform: translateY(-100vh) rotate(360deg);}
    }
  </style>
</head>
<body>
  <h1>💖 Special Surprise for Goomaral 💖</h1>
  <div id="countdown"></div>
  <button id="openBtn" style="display:none;">Open Message 🎀</button>
  <div id="message">🌸 Hi Goomaral! 🌸<br><br>
  You are one of the most special people.<br>
  Keep smiling and shining always 💕</div>

  <script>
    /* ========== Settings ========== */
    const unlockDate = new Date("2025-10-17T06:20:00"); // Local time (Mongolia)
    const countdown = document.getElementById("countdown");
    const openBtn = document.getElementById("openBtn");
    const message = document.getElementById("message");

    /* ========== Countdown Function ========== */
    const timer = setInterval(() => {
      const now = new Date();
      const diff = unlockDate - now;

      if (diff <= 0) {
        clearInterval(timer);
        countdown.textContent = "🎉 It's time! 🎉";
        openBtn.style.display = "inline-block";
      } else {
        const days = Math.floor(diff / (1000 * 60 * 60 * 24));
        const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
        const mins = Math.floor((diff / (1000 * 60)) % 60);
        const secs = Math.floor((diff / 1000) % 60);
        countdown.textContent = `${days}d ${hours}h ${mins}m ${secs}s`;
      }
    }, 1000);

    /* ========== Open Button Action ========== */
    openBtn.addEventListener("click", () => {
      countdown.style.display = "none";
      openBtn.style.display = "none";
      message.style.display = "block";

      for (let i = 0; i < 30; i++) {
        const heart = document.createElement("div");
        heart.className = "heart";
        heart.textContent = "💖";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.fontSize = Math.random() * 20 + 20 + "px";
        heart.style.animationDuration = Math.random() * 3 + 4 + "s";
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 5000);
      }
    });
  </script>
</body>
</html>
