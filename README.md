
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>subkazani.ir</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;500;600&display=swap" rel="stylesheet" />
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Vazirmatn', sans-serif;
      min-height: 100vh;
      background:
        radial-gradient(circle at 25% 15%, rgba(107, 33, 168, 0.30), transparent 55%),
        radial-gradient(circle at 85% 75%, rgba(59, 7, 100, 0.35), transparent 55%),
        linear-gradient(165deg, #000000 0%, #0a0510 25%, #170a29 50%, #250b45 75%, #38105f 100%);
      background-attachment: fixed;
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      overflow-x: hidden;
    }

    /* ---- Header (Telegram-channel style) ---- */
    .header {
      width: 100%;
      height: 140px;
      background: rgba(255, 255, 255, 0.04);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(168, 85, 247, 0.35);
      position: relative;
    }

    .avatar {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      position: absolute;
      left: 50%;
      bottom: -60px;
      transform: translateX(-50%);
      background: linear-gradient(135deg, #2d1052, #12071f);
      border: 3px solid #a855f7;
      box-shadow: 0 0 35px rgba(168, 85, 247, 0.55);
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .avatar img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    /* ---- Main content ---- */
    .content {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      text-align: center;
      padding: 96px 20px 0;
      gap: 18px;
    }

    .fa-text {
      font-size: clamp(1.6rem, 5vw, 2.6rem);
      font-weight: 600;
      background: linear-gradient(90deg, #e9d5ff, #a855f7, #7c3aed);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      animation: glow 4s ease-in-out infinite alternate;
    }

    .en-text {
      font-size: clamp(1rem, 3vw, 1.4rem);
      font-weight: 300;
      letter-spacing: 4px;
      color: rgba(233, 213, 255, 0.75);
      direction: ltr;
    }

    @keyframes glow {
      from { filter: drop-shadow(0 0 6px rgba(168, 85, 247, 0.3)); }
      to   { filter: drop-shadow(0 0 18px rgba(168, 85, 247, 0.8)); }
    }

    .divider {
      width: 55%;
      max-width: 260px;
      height: 1px;
      margin: 14px auto 6px;
      background: rgba(255, 255, 255, 0.65);
      box-shadow: 0 0 10px rgba(255, 255, 255, 0.45);
    }

    .quote-fa {
      max-width: 620px;
      font-size: clamp(1.1rem, 3.6vw, 1.5rem);
      font-weight: 500;
      line-height: 2;
      color: #e9d5ff;
      text-shadow: 0 0 14px rgba(168, 85, 247, 0.35);
    }

    /* ---- Morse Code with Circular Text ---- */
    .morse-container {
      max-width: 700px;
      margin-top: 40px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 30px;
    }

    .circular-morse {
      position: relative;
      width: 240px;
      height: 240px;
      cursor: pointer;
    }

    .morse-circle {
      width: 100%;
      height: 100%;
      border-radius: 50%;
      background: linear-gradient(135deg, rgba(168, 85, 247, 0.15), rgba(124, 58, 237, 0.1));
      border: 2px solid rgba(168, 85, 247, 0.5);
      box-shadow: 0 0 40px rgba(168, 85, 247, 0.3) inset, 0 0 30px rgba(168, 85, 247, 0.2);
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s ease;
      position: relative;
    }

    .circular-morse:hover .morse-circle {
      border-color: rgba(168, 85, 247, 0.8);
      box-shadow: 0 0 50px rgba(168, 85, 247, 0.5) inset, 0 0 40px rgba(168, 85, 247, 0.4);
      background: linear-gradient(135deg, rgba(168, 85, 247, 0.25), rgba(124, 58, 237, 0.2));
    }

    .morse-emoticon {
      font-size: 70px;
      font-weight: bold;
      color: #e9d5ff;
      text-shadow: 0 0 20px rgba(168, 85, 247, 0.6);
      user-select: none;
      transition: all 0.3s ease;
    }

    .circular-morse:hover .morse-emoticon {
      text-shadow: 0 0 30px rgba(233, 213, 255, 1);
      transform: scale(1.1);
    }

    .morse-circle::before {
      content: '';
      position: absolute;
      width: 100%;
      height: 100%;
      border-radius: 50%;
      animation: pulse 2s ease-in-out infinite;
      border: 2px solid rgba(168, 85, 247, 0.3);
      opacity: 0;
    }

    @keyframes pulse {
      0%, 100% {
        transform: scale(1);
        opacity: 0;
      }
      50% {
        transform: scale(1.15);
        opacity: 1;
      }
    }

    .circular-morse:hover .morse-circle::before {
      animation: pulse 1.5s ease-in-out infinite;
    }

    /* SVG Text on Circle */
    .morse-text-svg {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }

    .morse-text-svg text {
      font-family: 'Courier New', monospace;
      font-size: 14px;
      font-weight: 700;
      fill: rgba(255, 255, 255, 0.8);
      text-shadow: 0 0 8px rgba(255, 255, 255, 0.5);
      letter-spacing: 1px;
    }

    .morse-text-svg text:hover {
      fill: rgba(233, 213, 255, 1);
      filter: drop-shadow(0 0 8px rgba(168, 85, 247, 0.8));
    }

    /* ---- Empty gap before footer ---- */
    .gap-footer {
      width: 100%;
      min-height: 65vh;
      display: flex;
      align-items: flex-end;
      justify-content: center;
      padding-bottom: 36px;
    }

    .footer {
      font-size: 0.85rem;
      letter-spacing: 2px;
      color: rgba(255, 255, 255, 0.3);
      direction: ltr;
    }

    .footer a {
      color: rgba(192, 132, 252, 0.55);
      text-decoration: none;
      transition: color 0.4s ease, text-shadow 0.4s ease;
    }

    .footer a:hover {
      color: #c084fc;
      text-shadow: 0 0 10px rgba(192, 132, 252, 0.6);
    }

    /* Playing state indicator */
    .playing-indicator {
      position: fixed;
      bottom: 30px;
      left: 30px;
      font-size: 14px;
      color: rgba(168, 85, 247, 0.7);
      display: none;
      animation: blink 0.6s ease-in-out infinite;
    }

    @keyframes blink {
      0%, 49%, 100% { opacity: 1; }
      50%, 99% { opacity: 0.3; }
    }

    .playing-indicator.active {
      display: block;
    }
  </style>
</head>
<body>
  <audio id="morseAudio" src="Music.mp3" preload="auto"></audio>

  <header class="header">
    <div class="avatar">
      <!-- عکس خودت رو با اسم avatar.jpg کنار این فایل بذار -->
      <img src="avatar.jpg" alt="avatar" onerror="this.style.display='none'" />
    </div>
  </header>

  <main class="content">
    <div class="fa-text">شاید در زندگی بعدی</div>
    <div class="en-text">maybe in the next life</div>

    <div class="divider"></div>

    <div class="quote-fa">گاهی یک جنگ برای ماندن محترم از یک صلح است برای رفتن</div>
    <div class="en-text">Sometimes a war fought to stay is more honorable than a peace made to leave.</div>

    <!-- Morse Code with Circular Text -->
    <div class="morse-container">
      <div class="circular-morse" id="morseButton">
        <svg class="morse-text-svg" viewBox="0 0 240 240">
          <defs>
            <path id="circle" d="M 120, 120 m -105, 0 a 105,105 0 1,1 210,0 a 105,105 0 1,1 -210,0" fill="none" />
          </defs>
          <text font-size="11" font-weight="700" fill="rgba(255,255,255,0.75)" letter-spacing="1">
            <textPath href="#circle" startOffset="0%" text-anchor="start">
              🎵 PLAY ME &nbsp;•&nbsp; اضغط علي &nbsp;•&nbsp; 我来播放 &nbsp;•&nbsp; क्लिक करे &nbsp;•&nbsp; クリック &nbsp;•&nbsp; Klik Mig &nbsp;•&nbsp; 🎵 PLAY ME
            </textPath>
          </text>
        </svg>
        <div class="morse-circle">
          <div class="morse-emoticon">:(</div>
        </div>
      </div>
    </div>
  </main>

  <div class="gap-footer">
    <footer class="footer">
      <a href="https://subkazani.ir">subkazani.ir</a>
    </footer>
  </div>

  <div class="playing-indicator" id="playingIndicator">🎵 در حال پخش...</div>

  <script>
    // جابه‌جایی و کوچیک شدن تدریجی آواتار، متناسب با میزان اسکرول کاربر
    const avatarEl = document.querySelector('.avatar');
    const scrollRange = 220;
    const minScale = 0.55;
    
    function updateAvatarPosition() {
      const progress = Math.min(Math.max(window.scrollY / scrollRange, 0), 1);
      const leftPercent = 50 + progress * 30;
      const scale = 1 - progress * (1 - minScale);
      avatarEl.style.left = leftPercent + '%';
      avatarEl.style.transform = `translateX(-50%) scale(${scale})`;
    }
    
    window.addEventListener('scroll', () => {
      requestAnimationFrame(updateAvatarPosition);
    });
    updateAvatarPosition();

    // موسیقی - کلیک روی دایره کد مورس
    const morseButton = document.getElementById('morseButton');
    const morseAudio = document.getElementById('morseAudio');
    const playingIndicator = document.getElementById('playingIndicator');

    morseButton.addEventListener('click', (e) => {
      e.preventDefault();
      
      if (morseAudio.paused) {
        morseAudio.play()
          .then(() => {
            playingIndicator.classList.add('active');
          })
          .catch(() => {
            console.log('خطا در پخش صدا');
          });
      } else {
        morseAudio.pause();
        morseAudio.currentTime = 0;
        playingIndicator.classList.remove('active');
      }
    });

    morseAudio.addEventListener('ended', () => {
      playingIndicator.classList.remove('active');
    });
  </script>
</body>
</html>
