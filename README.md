<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Bonet Terminal - Hacker Chiến</title>
  <style>
    body {
      background-color: black;
      color: #00FF00;
      font-family: monospace;
      font-size: 14px;
      margin: 0;
      padding: 10px;
    }

    #terminal {
      height: 75vh;
      overflow-y: auto;
      white-space: pre-wrap;
      padding-bottom: 10px;
    }

    #inputLine {
      display: flex;
      align-items: center;
    }

    #prompt {
      color: #0f0;
      margin-right: 5px;
    }

    #userInput {
      background: black;
      border: none;
      color: #0f0;
      font-family: monospace;
      font-size: 14px;
      outline: none;
      flex: 1;
    }

    .ascii {
      display: none;
      color: red;
      font-size: 12px;
      white-space: pre;
      margin: 20px 0;
    }

    button {
      background: #000;
      color: #0f0;
      border: 1px solid #0f0;
      padding: 5px 10px;
      cursor: pointer;
      font-family: monospace;
      margin-bottom: 10px;
    }

    button:hover {
      background: #0f0;
      color: #000;
    }
  </style>
</head>
<body>
  <button onclick="toggleJoker()">🎭 Bật/Tắt Mặt Nạ JOKER</button>

  <div class="ascii" id="jokerMask">
  ██████╗██╗  ██╗██╗██╗  ███████╗███╗   ██╗
 ██╔════╝██║  ██║██║██║  ██╔════╝████╗  ██║
 ██║     ███████║██║██║  █████╗  ██╔██╗ ██║
 ██║     ██╔══██║██║██║  ██╔══╝  ██║╚██╗██║
 ╚██████╗██║  ██║██║███████╗██████╔╝ ╚████║
  ╚═════╝╚═╝  ╚═╝╚═╝╚══════╝╚═════╝   ╚═══╝

😈 JOKER MODE ACTIVATED - HACKER CHIẾN 💀
💣 BONET SYSTEM RUNNING...
  </div>

  <div id="terminal"></div>

  <div id="inputLine">
    <span id="prompt">Chiến@bonet:~$</span>
    <input type="text" id="userInput" autofocus autocomplete="off" />
  </div>

  <script>
    const terminal = document.getElementById("terminal");
    const input = document.getElementById("userInput");
    const jokerMask = document.getElementById("jokerMask");

    const logs = [
      "[+] DDoS attack launched on 104.21.77.1:80",
      "[+] Node 45.1.2.3 online. Injecting payload...",
      "[+] Exfiltrating credentials from 10.0.0.5",
      "[+] Uploading shell to /var/www/html/shell.php",
      "[+] AES-256 encryption enabled...",
      "[+] SSH brute force started...",
      "[+] Joker.exe is running silently..."
    ];

    const attackedWebsites = [
      "🔻 http://gov-vn.official-site.vn",
      "🔻 http://schoolportal.edu.vn",
      "🔻 http://banksecure.vn",
      "🔻 http://vps-cloud.net",
      "🔻 http://chat-ai-bot.site",
      "🔻 http://zalo-mini-hack.vn",
      "🔻 http://garena-login-verify.com",
      "🔻 http://hacker-zone.dev",
      "🔻 http://admin-panel.vn",
      "🔻 http://fb-check.info"
    ];

    let webIndex = 0;

    input.addEventListener("keydown", function (e) {
      if (e.key === "Enter") {
        const value = input.value.trim();
        terminal.innerHTML += `\nChiến@bonet:~$ ${value}`;
        input.value = "";
        simulateCommand(value);
        scrollBottom();
      }
    });

    function randomLog() {
      const log = logs[Math.floor(Math.random() * logs.length)];
      terminal.innerHTML += "\n" + log;
      scrollBottom();
    }

    function showAttackedWebsites() {
      if (webIndex < attackedWebsites.length) {
        terminal.innerHTML += `\n[ATTACKED] ${attackedWebsites[webIndex++]}`;
        scrollBottom();
      } else {
        webIndex = 0;
      }
    }

    setInterval(randomLog, 3000);
    setInterval(showAttackedWebsites, 5000);

    function simulateCommand(cmd) {
      if (cmd === "help") {
        terminal.innerHTML += "\nLệnh khả dụng:\n- ddos\n- scan\n- joker\n- clear\n- status\n- listweb";
      } else if (cmd === "ddos") {
        terminal.innerHTML += "\n[!] DDoS target 203.0.113.1 port 80 - Flooding...";
      } else if (cmd === "scan") {
        terminal.innerHTML += "\n[+] Scanning open ports: 21, 22, 80, 443...";
      } else if (cmd === "joker") {
        toggleJoker();
      } else if (cmd === "status") {
        terminal.innerHTML += "\n[+] BONET ACTIVE - 6 zombie nodes connected.";
      } else if (cmd === "listweb") {
        terminal.innerHTML += "\n[+] Danh sách website đã bị tấn công:";
        attackedWebsites.forEach(w => terminal.innerHTML += `\n[!] ${w}`);
      } else if (cmd === "clear") {
        terminal.innerHTML = "";
      } else {
        terminal.innerHTML += `\nCommand '${cmd}' not found. Gõ 'help' để xem.`;
      }
    }

    function scrollBottom() {
      terminal.scrollTop = terminal.scrollHeight;
    }

    function toggleJoker() {
      jokerMask.style.display = jokerMask.style.display === "block" ? "none" : "block";
      terminal.innerHTML += "\n[+] JOKER MODE " + (jokerMask.style.display === "block" ? "ON" : "OFF");
      scrollBottom();
    }
  </script>
</body>
</html>
