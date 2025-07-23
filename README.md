# runeworx_ai_dashboard
“Norse-themed AI command center powered by GPT”
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Rune Worx AI Dashboard</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>⚡ Rune Worx AI Dashboard</h1>
  </header>
  <main>
    <section id="gpt-console">
      <textarea id="user-input" placeholder="Speak 'Thor’s Welcome' to begin..."></textarea>
      <button id="send-btn">Invoke GPT</button>
      <div id="gpt-output"></div>
    </section>
    <!-- Future sections: Vault, Uploader, Status Board -->
  </main>
  <script src="config.js"></script>
  <script src="script.js"></script>
</body>
</html>
body {
  background: #0a0a0a;
  color: #ddd;
  font-family: 'Courier New', monospace;
  margin: 0;
  padding: 0;
}
header {
  background: #111;
  padding: 1rem;
  text-align: center;
  color: gold;
  font-size: 1.5rem;
}
#gpt-console {
  margin: 2rem auto;
  max-width: 600px;
}
#user-input {
  width: 100%;
  height: 80px;
  background: #222;
  color: #eee;
  border: 2px solid gold;
  padding: 0.5rem;
}
#send-btn {
  margin-top: 0.5rem;
  padding: 0.5rem 1rem;
  background: gold;
  border: none;
  cursor: pointer;
}
#gpt-output {
  margin-top: 1rem;
  background: #111;
  border: 1px solid #333;
  padding: 1rem;
  min-height: 150px;
}
document.getElementById('send-btn').addEventListener('click', async () => {
  const text = document.getElementById('user-input').value.trim();
  if (!text.toLowerCase().includes("thor’s welcome")) {
    document.getElementById('gpt-output').textContent = "⚠️ Speak the sacred words: Thor’s Welcome";
    return;
  }

  document.getElementById('gpt-output').textContent = "⚡ Summoning Odin’s insight...";
  
  const resp = await fetch(OPENAI_API_URL, {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "Authorization": "Bearer " + YOUR_API_TOKEN  // store your real token securely via Secrets
    },
    body: JSON.stringify({
      model: "gpt-4o",
      messages: [
        {role: "system", content: "You are Rune Worx's Norse-inspired assistant."},
        {role: "user", content: text}
      ]
    })
  });
  const data = await resp.json();
  document.getElementById('gpt-output').textContent = data.choices?.[0]?.message?.content || "Something went wrong.";
});
# Rune Worx AI Dashboard

A Norse-themed AI dashboard that invokes GPT‑4 with the sacred phrase **Thor’s Welcome**.

## 🚀 Quick Start

1. **Clone** this repo
2. Add your OpenAI token securely (via GitHub Codespaces secrets or input prompt)
3. In Codespaces, run a local server (e.g. `npx http-server`)
4. Deploy using GitHub Pages or Netlify

## 🔮 Next Steps

- Add Vault section for API secrets
- Integrate Ko‑fi / Gumroad feeds
- Add Status Board for tasks & revenue
- Automate with GitHub Actions + Zapier

