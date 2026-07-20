
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>subkazani.ir</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;500;600&family=Noto+Nastaliq+Urdu:wght@400;600;700&family=Cinzel:wght@500;600&display=swap" rel="stylesheet" />
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; }

    body {
      font-family: 'Vazirmatn', sans-serif;
      min-height: 100vh;
      background-color: #050202;
      background-image:
        radial-gradient(circle at 25% 15%, rgba(139, 0, 0, 0.30), transparent 55%),
        radial-gradient(circle at 85% 75%, rgba(90, 5, 5, 0.34), transparent 55%),
        linear-gradient(165deg, #000000 0%, #0d0303 25%, #1c0505 50%, #2b0505 75%, #3d0808 100%);
      background-attachment: fixed;
      background-size: cover;
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      overflow-x: hidden;
      position: relative;
    }

    /* پس‌زمینه سفارشی back.jpg در صورت وجود */
    body.custom-bg {
      background-image: url('back.jpg');
      background-size: cover;
      background-position: center;
      background-attachment: fixed;
    }

    /* ---- لایه کهکشانی (ستاره‌ها) ---- */
    #stars {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }
    .star {
      position: absolute;
      border-radius: 50%;
      background: #d8e6ff;
      box-shadow: 0 0 6px 1px rgba(190, 210, 255, 0.95);
      animation: twinkle ease-in-out infinite;
    }

    @keyframes twinkle {
      0%, 100% { opacity: var(--base-opacity); transform: scale(1); }
      50% { opacity: 1; transform: scale(1.35); }
    }

    body.custom-bg #stars { display: none; }

    /* همه بخش‌های محتوا بالای لایه ستاره‌ها */
    .header, .content, .gap-footer { position: relative; z-index: 1; }

    /* ---- هدر سبک کانال تلگرامی ---- */
    .header {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 34px 20px 0;
    }

    .long-line {
      width: 88%;
      max-width: 520px;
      height: 1.5px;
      margin-bottom: 30px;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.55) 20%, rgba(255, 255, 255, 0.55) 80%, transparent);
      box-shadow: 0 0 8px rgba(255, 255, 255, 0.3);
    }

    .avatar-frame {
      width: 176px;
      height: 176px;
      padding: 9px;
      border-radius: 26px;
      background: linear-gradient(145deg, #4a0808 0%, #0a0202 45%, #6e0f0f 75%, #1a0303 100%);
      box-shadow:
        0 16px 34px rgba(0, 0, 0, 0.65),
        0 0 28px rgba(139, 0, 0, 0.45),
        inset 0 1px 1px rgba(255, 255, 255, 0.12),
        inset 0 -2px 6px rgba(0, 0, 0, 0.5);
    }

    .avatar {
      position: relative;
      width: 100%;
      height: 100%;
      border-radius: 50%;
      overflow: hidden;
      background: radial-gradient(circle at 32% 28%, #5c0e0e, #0a0101 75%);
      box-shadow:
        inset 0 0 22px rgba(0, 0, 0, 0.65),
        inset 0 2px 3px rgba(255, 255, 255, 0.15);
    }

    .avatar::after {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 50%;
      background: radial-gradient(circle at 30% 22%, rgba(255, 255, 255, 0.30), transparent 45%);
      mix-blend-mode: overlay;
      pointer-events: none;
    }

    .avatar img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
    }

    .channel-name {
      margin-top: 16px;
      font-size: 1.15rem;
      font-weight: 600;
      letter-spacing: 1.5px;
      direction: ltr;
      background: linear-gradient(90deg, #ffffff, #e8b4b4 45%, #ffffff);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      text-shadow: 0 0 18px rgba(139, 0, 0, 0.35);
    }

    /* ---- محتوای اصلی ---- */
    .content {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      padding: 46px 20px 0;
    }

    .quote-box {
      padding: 20px 30px;
      border: 0.6px solid rgba(255, 255, 255, 0.22);
      border-radius: 6px;
      background: rgba(255, 255, 255, 0.015);
    }

    .fa-nastaliq {
      font-family: 'Noto Nastaliq Urdu', serif;
      font-size: clamp(1.35rem, 4.2vw, 1.9rem);
      font-weight: 600;
      color: #f2e4e4;
      margin-bottom: 10px;
      text-shadow: 0 0 14px rgba(139, 0, 0, 0.45);
    }

    .en-text {
      font-size: clamp(0.95rem, 2.8vw, 1.2rem);
      font-weight: 300;
      letter-spacing: 3px;
      color: rgba(255, 255, 255, 0.7);
      direction: ltr;
    }

    /* ---- دایره‌های موسیقی، هرکدوم توی یه ردیف جدا ---- */
    .morse-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 92px;
      margin: 58px 0 30px;
      width: 100%;
    }

    .music-row {
      display: flex;
      align-items: center;
      justify-content: center;
      direction: ltr;
      gap: 22px;
      width: 100%;
      max-width: 480px;
      padding: 0 16px;
    }

    .row-text-left { flex-direction: row; }
    .row-text-right { flex-direction: row-reverse; }
    .row-no-text { justify-content: flex-start; }

    .side-caption {
      max-width: 150px;
      text-align: center;
      direction: rtl;
      flex-shrink: 0;
    }

    .side-caption .fa-nastaliq {
      font-size: clamp(0.95rem, 3.4vw, 1.2rem);
      margin-bottom: 6px;
    }

    .side-caption .en-text {
      font-size: clamp(0.7rem, 2.2vw, 0.85rem);
      letter-spacing: 1.5px;
    }

    .circular-morse {
      position: relative;
      width: 140px;
      height: 140px;
      cursor: pointer;
      flex-shrink: 0;
    }

    .morse-text-svg {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      animation: spin 26s linear infinite;
    }

    @keyframes spin {
      from { transform: rotate(0deg); }
      to   { transform: rotate(360deg); }
    }

    .morse-text-svg text {
      font-family: 'Cinzel', serif;
      font-size: 8.5px;
      font-weight: 600;
      letter-spacing: 2px;
      fill: rgba(255, 255, 255, 0.55);
    }

    .morse-circle {
      position: absolute;
      inset: 20px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: radial-gradient(circle at 33% 28%, #6e0f0f, #0a0101 78%);
      box-shadow:
        0 12px 26px rgba(0, 0, 0, 0.6),
        0 0 24px rgba(139, 0, 0, 0.5),
        inset 0 2px 4px rgba(255, 255, 255, 0.14),
        inset 0 -6px 12px rgba(0, 0, 0, 0.55);
      transition: transform 0.25s ease, box-shadow 0.25s ease;
    }

    .morse-circle::after {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 50%;
      background: radial-gradient(circle at 30% 24%, rgba(255, 255, 255, 0.28), transparent 45%);
      mix-blend-mode: overlay;
      pointer-events: none;
    }

    .circular-morse:hover .morse-circle {
      transform: scale(1.06);
      box-shadow:
        0 14px 30px rgba(0, 0, 0, 0.65),
        0 0 34px rgba(139, 0, 0, 0.7),
        inset 0 2px 4px rgba(255, 255, 255, 0.16),
        inset 0 -6px 12px rgba(0, 0, 0, 0.55);
    }

    .morse-symbol {
      font-size: 2.1rem;
      color: #fff;
      text-shadow: 0 0 10px rgba(255, 255, 255, 0.55), 0 0 22px rgba(139, 0, 0, 0.85);
      user-select: none;
    }

    /* ---- فوتر ---- */
    .gap-footer {
      flex: 1;
      width: 100%;
      display: flex;
      align-items: flex-end;
      justify-content: center;
    }

    .footer {
      text-align: center;
      padding: 30px 16px 26px;
      font-size: 0.65rem;
      letter-spacing: 0.5px;
      color: rgba(255, 255, 255, 0.4);
      direction: ltr;
    }

    /* ---- نشانگر پخش ---- */
    .playing-indicator {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%) translateY(20px);
      background: rgba(20, 3, 3, 0.85);
      border: 1px solid rgba(139, 0, 0, 0.5);
      padding: 8px 18px;
      border-radius: 20px;
      font-size: 0.8rem;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease, transform 0.3s ease;
      z-index: 5;
    }
    .playing-indicator.active {
      opacity: 1;
      transform: translateX(-50%) translateY(0);
    }
  </style>
</head>
<body>

  <audio id="morseAudio" src="Music.mp3" preload="auto"></audio>
  <audio id="aktorAudio" src="aktor.mp3" preload="auto"></audio>
  <audio id="totoAudio" src="toto.mp3" preload="auto"></audio>
  <audio id="extraAudio" src="extra.mp3" preload="auto"></audio>

  <div id="stars"></div>

  <header class="header">
    <div class="long-line"></div>
    <div class="avatar-frame">
      <div class="avatar" id="avatar">
        <img src="avatar.jpg" alt="avatar" onerror="this.style.display='none'" />
      </div>
    </div>
  </header>

  <main class="content">
    <div class="quote-box">
      <div class="fa-nastaliq">شاید در زندگی بعدی</div>
      <div class="en-text">maybe in the next life</div>
    </div>

    <div class="morse-container">

      <!-- ردیف ۱: دایره سمت راست، متن سمت چپ -->
      <div class="music-row row-text-left">
        <div class="side-caption">
          <div class="fa-nastaliq">گاهی جنگ برای ماندن محترم‌تر از صلح است برای رفتن</div>
          <div class="en-text">Sometimes a war fought to stay is more honorable than a peace made to leave.</div>
        </div>
        <div class="circular-morse" id="morseButton">
          <svg class="morse-text-svg" viewBox="0 0 240 240">
            <defs>
              <path id="circlePath1" d="M 120, 120 m -105, 0 a 105,105 0 1,1 210,0 a 105,105 0 1,1 -210,0" fill="none" />
            </defs>
            <text>
              <textPath href="#circlePath1" startOffset="0%" text-anchor="start">
                &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp;
              </textPath>
            </text>
          </svg>
          <div class="morse-circle">
            <div class="morse-symbol">ꕥ</div>
          </div>
        </div>
      </div>

      <!-- ردیف ۲: دایره سمت چپ، متن سمت راست -->
      <div class="music-row row-text-right">
        <div class="side-caption">
          <div class="fa-nastaliq">به قول ون‌گوگ، غم همیشه باقیه</div>
          <div class="en-text">As Van Gogh said, the sadness always remains.</div>
        </div>
        <div class="circular-morse" id="aktorButton">
          <svg class="morse-text-svg" viewBox="0 0 240 240">
            <defs>
              <path id="circlePath2" d="M 120, 120 m -105, 0 a 105,105 0 1,1 210,0 a 105,105 0 1,1 -210,0" fill="none" />
            </defs>
            <text>
              <textPath href="#circlePath2" startOffset="0%" text-anchor="start">
                &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp;
              </textPath>
            </text>
          </svg>
          <div class="morse-circle">
            <div class="morse-symbol">ꕥ</div>
          </div>
        </div>
      </div>

      <!-- ردیف ۳: دایره سمت راست، متن سمت چپ -->
      <div class="music-row row-text-left">
        <div class="side-caption">
          <div class="fa-nastaliq">تو خودت خواستی !</div>
          <div class="en-text">You wanted it yourself!</div>
        </div>
        <div class="circular-morse" id="totoButton">
          <svg class="morse-text-svg" viewBox="0 0 240 240">
            <defs>
              <path id="circlePath3" d="M 120, 120 m -105, 0 a 105,105 0 1,1 210,0 a 105,105 0 1,1 -210,0" fill="none" />
            </defs>
            <text>
              <textPath href="#circlePath3" startOffset="0%" text-anchor="start">
                &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp;
              </textPath>
            </text>
          </svg>
          <div class="morse-circle">
            <div class="morse-symbol">ꕥ</div>
          </div>
        </div>
      </div>

      <!-- ردیف ۴: فعلاً بدون متن، فقط دایره سمت چپ -->
      <div class="music-row row-no-text">
        <div class="circular-morse" id="extraButton">
          <svg class="morse-text-svg" viewBox="0 0 240 240">
            <defs>
              <path id="circlePath4" d="M 120, 120 m -105, 0 a 105,105 0 1,1 210,0 a 105,105 0 1,1 -210,0" fill="none" />
            </defs>
            <text>
              <textPath href="#circlePath4" startOffset="0%" text-anchor="start">
                &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp; MAYBE IN THE NEXT LIFE &nbsp;•&nbsp; MAYBE NEVER SEE YOU &nbsp;•&nbsp;
              </textPath>
            </text>
          </svg>
          <div class="morse-circle">
            <div class="morse-symbol">ꕥ</div>
          </div>
        </div>
      </div>

    </div>
  </main>

  <div class="gap-footer">
    <footer class="footer" id="siteFooter">Maybe never see you</footer>
  </div>

  <div class="playing-indicator" id="playingIndicator">در حال پخش...</div>

  <script>
    // ---- تشخیص back.jpg برای پس‌زمینه سفارشی ----
    (function () {
      const bgImg = new Image();
      bgImg.onload = function () {
        document.body.classList.add('custom-bg');
      };
      bgImg.onerror = function () {
        // back.jpg موجود نیست، همون حالت کهکشانی مشکی-قرمز باقی می‌مونه
      };
      bgImg.src = 'back.jpg';
    })();

    // ---- ساخت لایه ستاره‌های کهکشانی ----
    (function () {
      const starsContainer = document.getElementById('stars');
      const starCount = 180;
      for (let i = 0; i < starCount; i++) {
        const star = document.createElement('div');
        star.className = 'star';
        const size = Math.random() * 2.5 + 1.5;
        const baseOpacity = (Math.random() * 0.5 + 0.5).toFixed(2);
        star.style.width = size + 'px';
        star.style.height = size + 'px';
        star.style.top = Math.random() * 100 + '%';
        star.style.left = Math.random() * 100 + '%';
        star.style.setProperty('--base-opacity', baseOpacity);
        star.style.opacity = baseOpacity;
        star.style.animationDuration = (Math.random() * 3 + 2.5) + 's';
        star.style.animationDelay = (Math.random() * 4) + 's';
        starsContainer.appendChild(star);
      }
    })();

    // ---- پخش‌کننده‌های موسیقی ----
    const playingIndicator = document.getElementById('playingIndicator');

    const players = [
      { button: document.getElementById('morseButton'), audio: document.getElementById('morseAudio') },
      { button: document.getElementById('aktorButton'), audio: document.getElementById('aktorAudio') },
      { button: document.getElementById('totoButton'), audio: document.getElementById('totoAudio') },
      { button: document.getElementById('extraButton'), audio: document.getElementById('extraAudio') }
    ];

    function stopAll(except) {
      players.forEach((p) => {
        if (p.audio !== except) {
          p.audio.pause();
          p.audio.currentTime = 0;
        }
      });
    }

    players.forEach((p) => {
      p.button.addEventListener('click', (e) => {
        e.preventDefault();
        if (p.audio.paused) {
          stopAll(p.audio);
          p.audio.play()
            .then(() => playingIndicator.classList.add('active'))
            .catch(() => console.log('خطا در پخش صدا'));
        } else {
          p.audio.pause();
          p.audio.currentTime = 0;
          playingIndicator.classList.remove('active');
        }
      });

      p.audio.addEventListener('ended', () => {
        playingIndicator.classList.remove('active');
      });
    });
  </script>
</body>
</html>
