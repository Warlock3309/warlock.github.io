<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Alemano Games | Links Oficiais</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
<style>
  body {
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif;
    background: radial-gradient(circle at top, #0a0018, #000);
    color: #fff;
    min-height: 100vh;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  canvas#particles {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 0;
  }
  h1 {
    font-size: 2.5rem;
    margin-bottom: 10px;
    background: linear-gradient(90deg, #ff00cc, #00ffff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: glow 3s infinite alternate;
    z-index: 1;
  }
  @keyframes glow {
    from { text-shadow: 0 0 10px #ff00cc; }
    to   { text-shadow: 0 0 25px #00ffff; }
  }
  /* ==== ANIMAÇÃO SINCRONIZADA DE COR EM BOTÕES ==== */
  @keyframes colorShift {
    0%   { background: linear-gradient(90deg, #ff0077, #7700ff); }
    50%  { background: linear-gradient(90deg, #00eaff, #ff00aa); }
    100% { background: linear-gradient(90deg, #ff0077, #7700ff); }
  }
  p {
    font-size: 1.1rem;
    color: #aaa;
    margin-bottom: 40px;
    animation: fadeIn 2s ease;
    z-index: 1;
  }
  .links {
    display: flex;
    flex-direction: column;
    gap: 25px;
    width: 90%;
    max-width: 320px;
    z-index: 1;
  }
  .link {
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    color: #fff;
    font-weight: 600;
    border-radius: 40px;
    padding: 15px 25px;
    box-shadow: 0 8px 0 #450066, 0 0 15px rgba(255,0,180,0.7);
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    position: relative;
    opacity: 0;
    animation: slideUp 0.8s ease forwards, colorShift 3s infinite alternate;
  }
  .link:hover {
    transform: translateY(-5px);
    box-shadow: 0 12px 15px rgba(255,0,180,0.7), 0 8px 0 #450066;
  }
  .link:active {
    transform: translateY(6px);
    box-shadow: 0 0 0 #450066, 0 0 8px rgba(255,0,180,0.7);
  }
  .link:nth-child(1) { animation-delay: 0.2s; }
  .link:nth-child(2) { animation-delay: 0.4s; }
  .link:nth-child(3) { animation-delay: 0.6s; }
  .link:nth-child(4) { animation-delay: 0.8s; }
  .link:nth-child(5) { animation-delay: 1s; }
  @keyframes slideUp {
    from { transform: translateY(30px); opacity: 0; }
    to   { transform: translateY(0); opacity: 1; }
  }
  footer {
    margin-top: 50px;
    font-size: 0.9rem;
    color: #666;
    z-index: 1;
    animation: fadeIn 3s ease;
  }
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
</style>
</head>
<body>

  <canvas id="particles"></canvas>

  <h1>Alemano Games 🎮</h1>
  <p>Bem-vindo! Escolha sua plataforma favorita 👇</p>

  <div class="links">
    <a class="link" href="https://www.youtube.com/@alemanogames" target="_blank">🎥 YouTube</a>
    <a class="link" href="https://www.twitch.tv/alemanogames" target="_blank">🕹️ Twitch</a>
    <a class="link" href="https://www.instagram.com" target="_blank">📸 Instagram</a>
    <a class="link" href="https://www.tiktok.com/@alemanogames" target="_blank">🎬 TikTok</a>
    <a class="link" href="https://discord.gg/wSkQkfq3a" target="_blank">💬 Discord</a>
  </div>

  <footer>© 2025 Alemano Games | Todos os direitos reservados</footer>

  <script>
    const canvas = document.getElementById('particles');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    const particles = [];
    const numParticles = 80;
    for (let i = 0; i < numParticles; i++) {
      particles.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        size: Math.random() * 2 + 1,
        speedX: (Math.random() - 0.5) * 1.2,
        speedY: (Math.random() - 0.5) * 1.2,
        color: `hsl(${Math.random() * 360}, 100%, 60%)`
      });
    }
    function animateParticles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      for (let p of particles) {
        ctx.beginPath();
        ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
        ctx.fillStyle = p.color;
        ctx.fill();
        p.x += p.speedX;
        p.y += p.speedY;
        if (p.x < 0 || p.x > canvas.width) p.speedX *= -1;
        if (p.y < 0 || p.y > canvas.height) p.speedY *= -1;
      }
      requestAnimationFrame(animateParticles);
    }
    animateParticles();
    window.addEventListener('resize', () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    });
  </script>
</body>
</html>
