import qrcode
from zipfile import ZipFile

# Conteúdo HTML do site
html_content = """<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Julia & Alan ❤️</title>
  <style>
    body {
      margin: 0;
      font-family: 'Arial', sans-serif;
      background-color: #ffe6f0;
      color: #444;
      text-align: center;
      padding: 30px;
    }
    h1 {
      color: #d63384;
      font-size: 3em;
      margin-bottom: 0.2em;
    }
    .love-message {
      font-size: 1.2em;
      margin: 20px auto;
      max-width: 600px;
      color: #555;
      line-height: 1.6;
    }
    .counter {
      font-size: 1.5em;
      margin-top: 20px;
      color: #b30059;
    }
    .music {
      margin: 30px 0;
    }
    .qr-code {
      margin-top: 40px;
    }
    .qr-code img {
      width: 150px;
      height: 150px;
    }
    footer {
      margin-top: 50px;
      font-size: 0.9em;
      color: #888;
    }
  </style>
</head>
<body>
  <h1>Julia & Alan ❤️</h1>
  <div class="counter">
    Juntos há: <span id="timer">...</span>
  </div>
  <div class="love-message">
    Você é tudo pra mim, obrigado por enfrentar os momentos diários comigo,<br>
    obrigado por estar do meu lado me apoiando e sendo luz,<br>
    eu te amo infinitamente meu amor, você é tudo que pode existir.
  </div>
  <div class="music">
    <h3>Nossa música 🎵</h3>
    <iframe width="300" height="169" src="https://www.youtube.com/embed/9rlW2rUzyn0?autoplay=1&loop=1&playlist=9rlW2rUzyn0" 
            frameborder="0" allow="autoplay; encrypted-media" allowfullscreen>
    </iframe>
  </div>
  <div class="qr-code">
    <h3>Nos encontre no Instagram 💖</h3>
    <img src="qrcode_instagram.png" alt="QR Code Instagram">
  </div>
  <footer>
    Feito com amor 💕 | Criado por ChatGPT para Julia & Alan
  </footer>
  <script>
    const startDate = new Date("2025-04-13T00:00:00");
    const timerEl = document.getElementById("timer");
    function updateTimer() {
      const now = new Date();
      const diff = now - startDate;
      const days = Math.floor(diff / (1000 * 60 * 60 * 24));
      const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutes = Math.floor((diff / (1000 * 60)) % 60);
      const seconds = Math.floor((diff / 1000) % 60);
      timerEl.textContent = `${days} dias, ${hours}h ${minutes}m ${seconds}s`;
    }
    setInterval(updateTimer, 1000);
    updateTimer();
  </script>
</body>
</html>"""

# Salva o HTML
with open("index.html", "w", encoding="utf-8") as f:
    f.write(html_content)

# Gera o QR Code do Instagram
qr = qrcode.make("https://www.instagram.com/")
qr.save("qrcode_instagram.png")

# Cria o arquivo zip
with ZipFile("julia-e-alan-site.zip", "w") as zipf:
    zipf.write("index.html")
    zipf.write("qrcode_instagram.png")

print("✅ Arquivo zip 'julia-e-alan-site.zip' criado com sucesso!")
