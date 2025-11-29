<html lang="th">
<head>
  <meta charset="UTF-8" />
  <title>Check Up Your Team – มาสำรวจบรรยากาศทีมของคุณกันเถอะ</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --bg-gradient: radial-gradient(circle at top left, #fee2e2, #fde68a, #bfdbfe, #e9d5ff);
      --primary: #6366f1;
      --primary-soft: #eef2ff;
      --accent-pink: #fb7185;
      --accent-teal: #14b8a6;
      --accent-yellow: #facc15;
      --card-bg: #ffffff;
      --text-main: #111827;
      --text-soft: #6b7280;
      --shadow-soft: 0 18px 35px rgba(15, 23, 42, 0.12);
      --radius-xl: 22px;
    }

    * {
      box-sizing: border-box;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background: var(--bg-gradient);
      color: var(--text-main);
      display: flex;
      flex-direction: column;
    }

    .app-header {
      padding: 1.6rem 1.2rem 1.2rem;
      text-align: center;
    }

    .app-header-inner {
      max-width: 960px;
      margin: 0 auto;
      background: rgba(255, 255, 255, 0.92);
      border-radius: 999px;
      padding: 0.9rem 1.8rem;
      display: flex;
      flex-direction: column;
      gap: 0.4rem;
      box-shadow: 0 16px 35px rgba(15, 23, 42, 0.15);
      border: 1px solid rgba(255, 255, 255, 0.8);
    }

    @media (min-width: 640px) {
      .app-header-inner {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
      }
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 0.7rem;
      justify-content: center;
      flex-wrap: wrap;
    }

    .brand-badge {
      width: 44px;
      height: 44px;
      border-radius: 18px;
      background: conic-gradient(from 140deg, #f97316, #ec4899, #22c55e, #0ea5e9, #f97316);
      display: flex;
      align-items: center;
      justify-content: center;
      color: #f9fafb;
      font-weight: 800;
      font-size: 1.1rem;
      box-shadow: 0 10px 24px rgba(15, 23, 42, 0.25);
    }

    .brand-text h1 {
      margin: 0;
      font-size: 1.35rem;
      letter-spacing: 0.02em;
    }

    .brand-text span {
      font-size: 0.86rem;
      color: var(--text-soft);
    }

    .tagline {
      font-size: 0.85rem;
      color: var(--text-soft);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.4rem;
      margin-top: 0.2rem;
      flex-wrap: wrap;
    }

    .pill {
      padding: 0.18rem 0.7rem;
      border-radius: 999px;
      background: #ecfeff;
      color: #0f766e;
      font-size: 0.78rem;
      font-weight: 600;
      border: 1px solid #a5f3fc;
    }

    .pill-rainbow {
      background: linear-gradient(120deg, #f97316, #ec4899, #6366f1, #22c55e);
      color: white;
      border: none;
    }

    .app-container {
      flex: 1;
      max-width: 960px;
      width: 100%;
      margin: 0 auto 2.4rem;
      padding: 0 1rem;
      display: flex;
      justify-content: center;
      align-items: flex-start;
    }

    .screen {
      display: none;
      background: var(--card-bg);
      border-radius: var(--radius-xl);
      padding: 1.7rem 1.8rem 1.9rem;
      box-shadow: var(--shadow-soft);
      width: 100%;
      margin-top: 0.7rem;
      animation: fadeInUp 0.35s ease-out;
      position: relative;
      overflow: hidden;
      border: 1px solid rgba(255, 255, 255, 0.8);
    }

    .screen::before {
      content: "";
      position: absolute;
      inset: 0;
      background:
        radial-gradient(circle at top right, rgba(129, 140, 248, 0.2), transparent 55%),
        radial-gradient(circle at bottom left, rgba(248, 113, 113, 0.2), transparent 55%);
      opacity: 0.9;
      pointer-events: none;
    }

    .screen > * {
      position: relative;
      z-index: 1;
    }

    .screen.active {
      display: block;
    }

    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(12px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    h2 {
      margin-top: 0;
      display: flex;
      align-items: center;
      gap: 0.4rem;
    }

    h2::before {
      content: "🎨";
      font-size: 1.2rem;
    }

    .hint-list {
      margin-top: 0.6rem;
      padding-left: 1.2rem;
      font-size: 0.96rem;
      color: var(--text-soft);
    }

    .hint-list li {
      margin-bottom: 0.2rem;
    }

    .input-label {
      display: block;
      margin: 1.6rem 0 0.8rem;
      font-size: 0.95rem;
      font-weight: 600;
    }

    input[type="text"] {
      width: 100%;
      padding: 0.75rem 0.95rem;
      border-radius: 14px;
      border: 1px solid #dbe2ff;
      font-size: 0.95rem;
      background: #f9fafb;
      transition: border-color 0.15s ease, box-shadow 0.15s ease, background 0.15s;
    }

    input[type="text"]:focus {
      outline: none;
      border-color: var(--primary);
      background: #ffffff;
      box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.25);
    }

    .btn-primary,
    .btn-secondary {
      border: none;
      border-radius: 999px;
      padding: 0.7rem 1.8rem;
      font-size: 0.95rem;
      cursor: pointer;
      transition: transform 0.06s ease, box-shadow 0.12s ease, background 0.15s;
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      font-weight: 600;
    }

    .btn-primary {
      background: linear-gradient(120deg, #6366f1, #ec4899, #f97316);
      color: white;
      box-shadow: 0 14px 28px rgba(129, 140, 248, 0.7);
    }

    .btn-secondary {
      background: rgba(248, 250, 252, 0.95);
      color: #111827;
      border: 1px solid #e5e7eb;
    }

    .btn-primary:hover,
    .btn-secondary:hover {
      transform: translateY(-1px);
      box-shadow: 0 16px 32px rgba(15, 23, 42, 0.16);
    }

    .btn-primary:active,
    .btn-secondary:active {
      transform: translateY(0);
      box-shadow: none;
    }

    .btn-primary:disabled,
    .btn-secondary:disabled {
      opacity: 0.55;
      cursor: default;
      box-shadow: none;
      transform: none;
    }

    .question-header {
      margin-bottom: 1.1rem;
    }

    #question-progress {
      font-size: 0.85rem;
      color: var(--text-soft);
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 0.6rem;
      flex-wrap: wrap;
    }

    #question-progress span {
      font-weight: 600;
      color: #4b5563;
    }

    .progress-bar {
      flex: 1;
      height: 8px;
      border-radius: 999px;
      background: rgba(229, 231, 235, 0.9);
      overflow: hidden;
      position: relative;
    }

    .progress-bar-inner {
      height: 100%;
      width: 0;
      background: linear-gradient(90deg, #6366f1, #22c55e, #facc15);
      transition: width 0.25s ease;
    }

    .question-text {
      margin-top: 0.6rem;
      font-size: 1rem;
    }

    .options-container {
      display: grid;
      gap: 0.95rem;
      margin: 1.2rem 0 1.4rem;
    }

    .option-card {
      padding: 0.95rem 1rem;
      border-radius: 16px;
      border: 1px solid #e5e7eb;
      background: #f9fafb;
      cursor: pointer;
      font-size: 0.96rem;
      transition:
        background 0.1s ease,
        border-color 0.1s ease,
        transform 0.06s,
        box-shadow 0.12s ease;
      display: flex;
      gap: 0.75rem;
      align-items: flex-start;
    }

    .option-card:nth-child(1) .option-icon {
      background: #fee2e2;
    }
    .option-card:nth-child(2) .option-icon {
      background: #e0f2fe;
    }
    .option-card:nth-child(3) .option-icon {
      background: #fef3c7;
    }

    .option-icon {
      width: 30px;
      height: 30px;
      border-radius: 999px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.1rem;
      flex-shrink: 0;
    }

    .option-text {
      flex: 1;
    }

    .option-card:hover {
      background: #fdf2ff;
      border-color: #f0abfc;
      transform: translateY(-1px);
      box-shadow: 0 12px 24px rgba(148, 163, 184, 0.4);
    }

    .option-card.selected {
      background: linear-gradient(135deg, #6366f1, #ec4899, #f97316);
      color: #f9fafb;
      border-color: transparent;
      box-shadow: 0 16px 36px rgba(129, 140, 248, 0.75);
    }

    .option-card.selected .option-icon {
      background: rgba(248, 250, 252, 0.2);
    }

    .reflection-box {
      margin-top: 0.5rem;
      padding: 0.9rem 1rem;
      border-radius: 16px;
      background: rgba(239, 246, 255, 0.9);
      border: 1px dashed #bfdbfe;
    }

    .reflection-box label {
      font-size: 0.9rem;
      display: block;
      margin-bottom: 0.25rem;
      color: #1d4ed8;
      display: flex;
      align-items: center;
      gap: 0.3rem;
    }

    .reflection-box label::before {
      content: "💬";
    }

    textarea {
      width: 100%;
      padding: 0.6rem 0.8rem;
      border-radius: 12px;
      border: 1px solid #dbeafe;
      resize: vertical;
      font-size: 0.9rem;
      background: #ffffff;
      min-height: 64px;
    }

    textarea:focus {
      outline: none;
      border-color: #3b82f6;
      box-shadow: 0 0 0 2px rgba(59, 130, 246, 0.32);
    }

    .question-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 1.3rem;
      gap: 0.7rem;
      flex-wrap: wrap;
    }

    .question-footer span {
      font-size: 0.83rem;
      color: var(--text-soft);
    }

    .result-grid {
      display: grid;
      gap: 1rem;
      margin: 1.3rem 0;
    }

    @media (min-width: 720px) {
      .result-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }

    .result-card {
      border-radius: 18px;
      background: linear-gradient(135deg, #eef2ff, #fee2e2, #fef9c3);
      padding: 1rem 1.1rem;
      border: 1px solid rgba(209, 213, 219, 0.9);
      box-shadow: 0 12px 26px rgba(148, 163, 184, 0.35);
    }

    .result-card h3 {
      margin-top: 0;
      font-size: 1rem;
      display: flex;
      align-items: center;
      gap: 0.3rem;
    }

    .result-card .score {
      font-weight: 700;
      margin-bottom: 0.3rem;
    }

    .overall-box {
      background: linear-gradient(120deg, #ecfeff, #fef3c7);
      border-radius: 20px;
      padding: 1.1rem 1.2rem;
      margin-bottom: 1rem;
      border: 1px solid #bae6fd;
      box-shadow: 0 10px 24px rgba(59, 130, 246, 0.25);
    }

    .overall-box h3 {
      margin-top: 0;
      display: flex;
      align-items: center;
      gap: 0.3rem;
    }

    .overall-box h3::before {
      content: "🌈";
    }

    .app-footer {
      text-align: center;
      font-size: 0.8rem;
      color: var(--text-soft);
      margin-bottom: 1rem;
      padding: 0 1rem;
    }
  </style>
</head>
<body>
  <header class="app-header">
    <div class="app-header-inner">
      <div class="brand">
        <div class="brand-badge">C</div>
        <div class="brand-text">
          <h1>Check Up Your Team</h1>
          <span>มาสำรวจบรรยากาศทีมของคุณกันเถอะ 💬🤝</span>
        </div>
      </div>
      <div class="tagline">
        <span class="pill">ตอบแบบสบายใจ ไม่มีคำตอบผิด</span>
        <span class="pill pill-rainbow">สำหรับนักเรียน & ทีมสภานักเรียน</span>
      </div>
    </div>
  </header>

  <main class="app-container">

    <!-- หน้าต้อนรับ -->
    <section id="screen-start" class="screen active">
      <h2>เริ่มเช็กอัปทีมของคุณกันเลย 💡</h2>
      <p>
        เกมนี้มีสถานการณ์เกี่ยวกับการทำงานเป็นทีมทั้งหมด <strong>6 สถานการณ์</strong><br />
        แค่เลือกคำตอบที่ “ใกล้กับตัวตนของคุณที่สุด” แล้วระบบจะช่วยสะท้อนให้เห็นว่า<br />
        คุณรู้สึกปลอดภัยแค่ไหนเวลาอยู่ในทีม 😊
      </p>
      <ul class="hint-list">
        <li>ไม่มีคำตอบถูกหรือผิด ทุกคำตอบคือ “เวอร์ชันจริงของคุณ”</li>
        <li>ผลลัพธ์มีไว้เพื่อเรียนรู้และเติบโต ไม่ได้ใช้ตัดสินใคร</li>
        <li>ถ้าอยากแชร์ประสบการณ์ ก็พิมพ์เล่าในช่องสะท้อนคิดได้เลย</li>
      </ul>

      <label class="input-label">
        ชื่อเล่นของคุณ (เอาไว้เรียกในหน้าผลลัพธ์):
        <input type="text" id="player-name" placeholder="เช่น โบ, กานต์, เนย, ต้น" />
      </label>

      <button id="btn-start" class="btn-primary">
        <span>เริ่ม Check Up ทีมของฉัน</span> <span>▶</span>
      </button>
    </section>

    <!-- หน้าคำถาม -->
    <section id="screen-question" class="screen">
      <div class="question-header">
        <div id="question-progress">
          <span id="question-count"></span>
          <div class="progress-bar">
            <div id="progress-bar-inner" class="progress-bar-inner"></div>
          </div>
        </div>
        <h2 id="question-title"></h2>
        <p id="question-text" class="question-text"></p>
      </div>

      <div id="options-container" class="options-container">
        <!-- ตัวเลือกจะถูกใส่ด้วย JavaScript -->
      </div>

      <div class="reflection-box">
        <label for="reflection-input">ถ้ามีเหตุการณ์คล้าย ๆ แบบนี้ในชีวิตจริง คุณอยากเล่ายังไง? (ไม่บังคับ)</label>
        <textarea id="reflection-input" rows="3" placeholder="พิมพ์ความคิด/ความรู้สึกเพิ่มเติมได้ที่นี่..."></textarea>
      </div>

      <div class="question-footer">
        <button id="btn-prev" class="btn-secondary">
          ◀ ย้อนกลับ
        </button>
        <div>
          <span id="helper-text">เลือกคำตอบที่ใกล้ตัวคุณที่สุด แล้วกด “ข้อต่อไป”</span>
          <button id="btn-next" class="btn-primary">
            ข้อต่อไป ▶
          </button>
        </div>
      </div>
    </section>

    <!-- หน้าผลลัพธ์ -->
    <section id="screen-result" class="screen">
      <h2>ผลการ Check Up ทีมของคุณ 🎉</h2>
      <p id="result-intro"></p>

      <div class="result-grid">
        <div class="result-card">
          <h3>🗣 การกล้าแสดงความเห็น</h3>
          <p class="score" id="score-voice"></p>
          <p id="desc-voice"></p>
        </div>
        <div class="result-card">
          <h3>✨ การยอมรับความผิดพลาด</h3>
          <p class="score" id="score-error"></p>
          <p id="desc-error"></p>
        </div>
        <div class="result-card">
          <h3>🤝 ความเป็นเจ้าของร่วมในทีม</h3>
          <p class="score" id="score-inclusion"></p>
          <p id="desc-inclusion"></p>
        </div>
        <div class="result-card">
          <h3>💗 การสนับสนุนกันในทีม</h3>
          <p class="score" id="score-support"></p>
          <p id="desc-support"></p>
        </div>
      </div>

      <div class="overall-box">
        <h3>ภาพรวมบรรยากาศทีมของคุณ</h3>
        <p id="overall-text"></p>
      </div>

      <button id="btn-restart" class="btn-secondary">
        🔁 เล่นอีกครั้ง หรือให้เพื่อนลองเล่นดู
      </button>
    </section>

  </main>

  <footer class="app-footer">
    <small>Check Up Your Team – Prototype เพื่อการเรียนรู้ | สามารถต่อยอดเชื่อม AI วิเคราะห์ข้อความได้ในอนาคต 💡</small>
  </footer>

  <script>
    const scenarios = [
      {
        id: 1,
        title: "สถานการณ์ที่ 1: เสนอไอเดียในที่ประชุม",
        text: "ในที่ประชุมสภานักเรียน เพื่อนส่วนใหญ่ดูเห็นด้วยกับแนวทางหนึ่งที่คุณไม่ค่อยมั่นใจ คุณมีไอเดียอีกแบบที่ต่างออกไป คุณจะทำอย่างไร?",
        options: [
          {
            icon: "💡",
            text: "ยกมือเสนอไอเดียของตัวเองอย่างสุภาพ แม้จะต่างจากส่วนใหญ่",
            scores: { voice: 3, error: 2, inclusion: 2, support: 2 }
          },
          {
            icon: "👀",
            text: "รอดูว่ามีใครเสนอไอเดียคล้าย ๆ คุณไหม ถ้ามีก็ค่อยเสริม",
            scores: { voice: 2, error: 2, inclusion: 2, support: 2 }
          },
          {
            icon: "🤐",
            text: "เก็บไว้ก่อนเพราะกลัวเพื่อนมองว่าแย้งหรือขัดจังหวะ",
            scores: { voice: 1, error: 1, inclusion: 2, support: 1 }
          }
        ]
      },
      {
        id: 2,
        title: "สถานการณ์ที่ 2: ทำงานผิดพลาด",
        text: "คุณเป็นคนรับผิดชอบทำโปสเตอร์งานโรงเรียน แต่เผลอใส่วันผิด ทำให้ต้องแก้ใหม่ทั้งหมด คุณจะทำอย่างไร?",
        options: [
          {
            icon: "📣",
            text: "รีบบอกทีมและครูที่ปรึกษา ยอมรับว่าเป็นความผิดพลาดของตนเอง แล้วเสนอวิธีแก้",
            scores: { voice: 3, error: 3, inclusion: 2, support: 2 }
          },
          {
            icon: "🧩",
            text: "แก้ไขเงียบ ๆ แล้วส่งไฟล์ใหม่ โดยไม่เล่ารายละเอียดให้ทีมฟัง",
            scores: { voice: 2, error: 2, inclusion: 2, support: 1 }
          },
          {
            icon: "🙈",
            text: "พยายามให้คนอื่นช่วยรับผิดชอบร่วม เพื่อไม่ให้ตัวเองดูผิดคนเดียว",
            scores: { voice: 1, error: 1, inclusion: 1, support: 1 }
          }
        ]
      },
      {
        id: 3,
        title: "สถานการณ์ที่ 3: เพื่อนเงียบในทีม",
        text: "ในกลุ่มทำงาน มีเพื่อนคนหนึ่งไม่ค่อยพูดและเหมือนยังไม่เข้าใจหน้าที่ของตัวเอง คุณจะทำอย่างไร?",
        options: [
          {
            icon: "🧑‍🤝‍🧑",
            text: "ชวนคุยแบบส่วนตัว ถามว่าโอเคไหม และมีอะไรที่ทีมช่วยได้บ้าง",
            scores: { voice: 2, error: 2, inclusion: 3, support: 3 }
          },
          {
            icon: "⏳",
            text: "ปล่อยไปก่อน ถ้าเขามีปัญหาคงบอกเอง",
            scores: { voice: 2, error: 1, inclusion: 1, support: 1 }
          },
          {
            icon: "📢",
            text: "บอกเพื่อนในทีมคนอื่นว่าเขาไม่ค่อยช่วยงาน เพื่อให้คนอื่นระวัง",
            scores: { voice: 1, error: 1, inclusion: 1, support: 0 }
          }
        ]
      },
      {
        id: 4,
        title: "สถานการณ์ที่ 4: ได้รับคำวิจารณ์",
        text: "คุณนำเสนอไอเดียกิจกรรม แล้วเพื่อนคนหนึ่งวิจารณ์อย่างตรงไปตรงมาว่าบางส่วนยังไม่ชัด คุณรู้สึกอย่างไรและจะตอบสนองอย่างไร?",
        options: [
          {
            icon: "📝",
            text: "ขอบคุณสำหรับความคิดเห็น แล้วถามต่อว่าควรปรับตรงไหนบ้าง",
            scores: { voice: 3, error: 3, inclusion: 2, support: 2 }
          },
          {
            icon: "😶",
            text: "เงียบไป และพยายามเลี่ยงการเสนอไอเดียในครั้งต่อไป",
            scores: { voice: 1, error: 1, inclusion: 1, support: 1 }
          },
          {
            icon: "⚡",
            text: "ตอบโต้ทันทีว่าที่ทำมาก็ยากแล้ว ทำให้บรรยากาศเริ่มตึงเครียด",
            scores: { voice: 1, error: 1, inclusion: 1, support: 0 }
          }
        ]
      },
      {
        id: 5,
        title: "สถานการณ์ที่ 5: แบ่งงานไม่เท่ากัน",
        text: "ในกลุ่มมีบางคนได้งานเยอะมาก บางคนแทบไม่ต้องทำอะไร สมาชิกเริ่มบ่นในแชท คุณจะทำอย่างไร?",
        options: [
          {
            icon: "🧭",
            text: "เสนอให้ทีมคุยเรื่องแบ่งงานใหม่อย่างเปิดใจในที่ประชุมเล็ก ๆ",
            scores: { voice: 3, error: 2, inclusion: 3, support: 2 }
          },
          {
            icon: "💪",
            text: "พยายามช่วยรับงานเพิ่มเอง เพื่อไม่ให้เรื่องยืดเยื้อ",
            scores: { voice: 2, error: 2, inclusion: 2, support: 3 }
          },
          {
            icon: "🚶‍♂️",
            text: "ปล่อยไป เพราะไม่อยากยุ่งกับดราม่าของกลุ่ม",
            scores: { voice: 1, error: 1, inclusion: 1, support: 1 }
          }
        ]
      },
      {
        id: 6,
        title: "สถานการณ์ที่ 6: เสนอสิ่งใหม่ในทีมเดิม",
        text: "ทีมของคุณเคยทำกิจกรรมแบบเดิมมาหลายปี คุณมีไอเดียใหม่ที่อาจช่วยให้น่าสนใจกว่าเดิม แต่เสี่ยงต่อการลองของใหม่ คุณจะทำอย่างไร?",
        options: [
          {
            icon: "🚀",
            text: "ลองเสนอไอเดียใหม่ พร้อมยกตัวอย่างข้อดีข้อเสียให้ทีมพิจารณา",
            scores: { voice: 3, error: 2, inclusion: 2, support: 2 }
          },
          {
            icon: "🕰",
            text: "รอดูปีหน้าแล้วค่อยเสนอ เพราะกลัวว่าเปลี่ยนปีนี้จะวุ่นวาย",
            scores: { voice: 2, error: 2, inclusion: 2, support: 1 }
          },
          {
            icon: "🙊",
            text: "ไม่พูดอะไร เพราะคิดว่าทีมคงไม่อยากเปลี่ยนอยู่แล้ว",
            scores: { voice: 1, error: 1, inclusion: 1, support: 1 }
          }
        ]
      }
    ];

    let currentIndex = 0;
    let selectedOptions = Array(scenarios.length).fill(null);
    let reflections = Array(scenarios.length).fill("");

    const totalScores = {
      voice: 0,
      error: 0,
      inclusion: 0,
      support: 0
    };

    const screenStart = document.getElementById("screen-start");
    const screenQuestion = document.getElementById("screen-question");
    const screenResult = document.getElementById("screen-result");

    const btnStart = document.getElementById("btn-start");
    const btnPrev = document.getElementById("btn-prev");
    const btnNext = document.getElementById("btn-next");
    const btnRestart = document.getElementById("btn-restart");

    const questionCount = document.getElementById("question-count");
    const progressBarInner = document.getElementById("progress-bar-inner");
    const questionTitle = document.getElementById("question-title");
    const questionText = document.getElementById("question-text");
    const optionsContainer = document.getElementById("options-container");
    const reflectionInput = document.getElementById("reflection-input");
    const helperText = document.getElementById("helper-text");

    const resultIntro = document.getElementById("result-intro");
    const scoreVoice = document.getElementById("score-voice");
    const scoreError = document.getElementById("score-error");
    const scoreInclusion = document.getElementById("score-inclusion");
    const scoreSupport = document.getElementById("score-support");
    const descVoice = document.getElementById("desc-voice");
    const descError = document.getElementById("desc-error");
    const descInclusion = document.getElementById("desc-inclusion");
    const descSupport = document.getElementById("desc-support");
    const overallText = document.getElementById("overall-text");

    const playerNameInput = document.getElementById("player-name");

    function showScreen(screen) {
      [screenStart, screenQuestion, screenResult].forEach((s) =>
        s.classList.remove("active")
      );
      screen.classList.add("active");
      window.scrollTo({ top: 0, behavior: "smooth" });
    }

    btnStart.addEventListener("click", () => {
      const name = playerNameInput.value.trim();
      if (!name) {
        alert("กรุณากรอกชื่อเล่นเล็กน้อย เพื่อให้ผลลัพธ์เรียกคุณได้แบบกันเองนะครับ 🙂");
        return;
      }
      currentIndex = 0;
      selectedOptions.fill(null);
      reflections.fill("");
      resetTotalScores();
      renderQuestion();
      showScreen(screenQuestion);
    });

    function renderQuestion() {
      const scenario = scenarios[currentIndex];
      questionCount.textContent = `สถานการณ์ที่ ${currentIndex + 1} / ${scenarios.length}`;
      const progressPercent = (currentIndex / scenarios.length) * 100;
      progressBarInner.style.width = `${progressPercent}%`;

      questionTitle.textContent = scenario.title;
      questionText.textContent = scenario.text;

      optionsContainer.innerHTML = "";
      scenario.options.forEach((opt, idx) => {
        const card = document.createElement("div");
        card.className = "option-card";

        const iconEl = document.createElement("div");
        iconEl.className = "option-icon";
        iconEl.textContent = opt.icon || "⭐";

        const textWrapper = document.createElement("div");
        textWrapper.className = "option-text";
        textWrapper.textContent = opt.text;

        card.appendChild(iconEl);
        card.appendChild(textWrapper);

        if (selectedOptions[currentIndex] === idx) {
          card.classList.add("selected");
        }

        card.addEventListener("click", () => {
          selectedOptions[currentIndex] = idx;
          document
            .querySelectorAll(".option-card")
            .forEach((c) => c.classList.remove("selected"));
          card.classList.add("selected");
        });

        optionsContainer.appendChild(card);
      });

      reflectionInput.value = reflections[currentIndex] || "";

      btnPrev.disabled = currentIndex === 0;
      btnNext.textContent =
        currentIndex === scenarios.length - 1 ? "ดูผล Check Up 🎯" : "ข้อต่อไป ▶";

      helperText.textContent =
        currentIndex === scenarios.length - 1
          ? "ข้อนี้ข้อสุดท้ายแล้ว เลือกคำตอบแล้วกด “ดูผล Check Up” ได้เลย"
          : "เลือกคำตอบให้ใกล้ตัวคุณที่สุด แล้วกด “ข้อต่อไป”";
    }

    btnPrev.addEventListener("click", () => {
      saveReflection();
      if (currentIndex > 0) {
        currentIndex--;
        renderQuestion();
      }
    });

    btnNext.addEventListener("click", () => {
      saveReflection();

      if (selectedOptions[currentIndex] === null) {
        alert("ลองเลือกคำตอบสักข้อก่อนนะครับ ไม่มีคำตอบไหนผิดเลย 🙂");
        return;
      }

      if (currentIndex < scenarios.length - 1) {
        currentIndex++;
        renderQuestion();
      } else {
        calculateScores();
        renderResult();
        showScreen(screenResult);
      }
    });

    function saveReflection() {
      reflections[currentIndex] = reflectionInput.value.trim();
    }

    function resetTotalScores() {
      totalScores.voice = 0;
      totalScores.error = 0;
      totalScores.inclusion = 0;
      totalScores.support = 0;
    }

    function calculateScores() {
      resetTotalScores();
      selectedOptions.forEach((optIndex, qIndex) => {
        const scenario = scenarios[qIndex];
        const chosen = scenario.options[optIndex];
        totalScores.voice += chosen.scores.voice;
        totalScores.error += chosen.scores.error;
        totalScores.inclusion += chosen.scores.inclusion;
        totalScores.support += chosen.scores.support;
      });
    }

    function levelText(score, maxScore) {
      const percent = (score / maxScore) * 100;
      if (percent >= 75) return { label: "สูง", color: "🟢" };
      if (percent >= 50) return { label: "ปานกลาง", color: "🟡" };
      return { label: "ต้องการดูแล", color: "🔴" };
    }

    function renderResult() {
      const name = playerNameInput.value.trim() || "คุณ";
      const maxScorePerDim = scenarios.length * 3;

      const lvVoice = levelText(totalScores.voice, maxScorePerDim);
      const lvError = levelText(totalScores.error, maxScorePerDim);
      const lvInclusion = levelText(totalScores.inclusion, maxScorePerDim);
      const lvSupport = levelText(totalScores.support, maxScorePerDim);

      resultIntro.textContent = `${name} นี่คือภาพรวมสไตล์การอยู่ในทีมของคุณ ลองอ่านแบบไม่ตัดสินตัวเอง แล้วใช้เป็นไอเดียในการดูแลทั้งตัวเองและบรรยากาศทีมไปพร้อมกันนะครับ 🌈`;

      scoreVoice.textContent = `${totalScores.voice} / ${maxScorePerDim} (${lvVoice.color} ${lvVoice.label})`;
      scoreError.textContent = `${totalScores.error} / ${maxScorePerDim} (${lvError.color} ${lvError.label})`;
      scoreInclusion.textContent = `${totalScores.inclusion} / ${maxScorePerDim} (${lvInclusion.color} ${lvInclusion.label})`;
      scoreSupport.textContent = `${totalScores.support} / ${maxScorePerDim} (${lvSupport.color} ${lvSupport.label})`;

      descVoice.textContent =
        lvVoice.label === "สูง"
          ? "คุณค่อนข้างกล้าแสดงความเห็น และพร้อมเสนอไอเดียใหม่ ๆ เมื่อเห็นว่ามีประโยชน์ต่อทีม เป็นพลังสำคัญที่ช่วยให้ทีมไม่หยุดอยู่กับที่ 👏"
          : lvVoice.label === "ปานกลาง"
          ? "คุณกล้าแสดงความเห็นในบางสถานการณ์ โดยเฉพาะเมื่อรู้สึกว่าบรรยากาศปลอดภัย แปลว่าถ้าทีมช่วยกันเปิดพื้นที่ดี ๆ คุณจะกล้าเปล่งเสียงของตัวเองได้มากขึ้นอีกเยอะ 💬"
          : "คุณมักเก็บความคิดไว้ในใจ เพราะกลัวว่าพูดแล้วอาจทำให้คนอื่นไม่สบายใจ หรือกลัวถูกมองแปลกไป สิ่งนี้เข้าใจได้มาก แต่อย่าลืมว่าเสียงของคุณมีคุณค่าเสมอ ทีมอาจได้อะไรดี ๆ จากไอเดียของคุณก็ได้ 💡";

      descError.textContent =
        lvError.label === "สูง"
          ? "เมื่อเกิดความผิดพลาด คุณพร้อมยอมรับและมองเป็นโอกาสเรียนรู้ ซึ่งเป็นทักษะสำคัญของผู้นำและคนทำงานมืออาชีพในอนาคต ✨"
          : lvError.label === "ปานกลาง"
          ? "คุณพอรับมือกับความผิดพลาดได้ แต่บางครั้งยังรู้สึกกลัวสายตาคนอื่น สิ่งนี้เป็นเรื่องธรรมดามาก หากทีมช่วยกันยอมรับความผิดพลาดได้มากขึ้น คุณจะรู้สึกสบายใจกับการลองสิ่งใหม่ ๆ มากขึ้นด้วย 💭"
          : "คุณอาจรู้สึกเครียดหรือโทษตัวเองเมื่อทำผิด ทำให้พยายามหลีกเลี่ยงการพูดถึงความผิดพลาดของตัวเอง นี่ไม่ใช่ข้อด้อยของคุณ แต่เป็นสัญญาณว่าทีมอาจต้องสร้างพื้นที่ที่อ่อนโยนต่อการผิดพลาดให้มากขึ้น 💗";

      descInclusion.textContent =
        lvInclusion.label === "สูง"
          ? "คุณให้ความสำคัญกับการดึงทุกคนให้มีส่วนร่วม และมองว่าทีมที่ดีคือทีมที่ทุกคนรู้สึกเป็นเจ้าของร่วมกัน พลังแบบนี้ทำให้ทีมอบอุ่นและอยู่ด้วยแล้วสบายใจมาก 🤝"
          : lvInclusion.label === "ปานกลาง"
          ? "คุณมองเห็นความสำคัญของการมีส่วนร่วม แต่บางครั้งอาจยังไม่ค่อยกล้าเข้าไปชวนหรือสะกิดเพื่อนที่เงียบเท่าไร ถ้าลองเริ่มจากประโยคง่าย ๆ อย่าง “คิดว่ายังไงบ้าง” ก็ช่วยเปิดพื้นที่ให้เพื่อนรู้สึกเป็นส่วนหนึ่งได้เยอะเลย 😊"
          : "คุณอาจยังไม่ค่อยเข้าไปจัดการเมื่อเห็นเพื่อนบางคนถูกกันออกจากวง หรือไม่ได้มีส่วนร่วม สิ่งนี้เข้าใจได้เพราะหลายครั้งเราก็กลัวดราม่า แต่ถ้าคุณเริ่มต้นจากการเป็นคนรับฟังเพื่อนเงียบ ๆ แค่หนึ่งคน นั่นก็ถือว่าเป็นก้าวที่สำคัญมากแล้ว 🌱";

      descSupport.textContent =
        lvSupport.label === "สูง"
          ? "คุณมักเป็นคนที่คอยสนับสนุนเพื่อน พร้อมช่วยเหลือเมื่อเห็นว่าคนอื่นลำบาก คนแบบคุณคือหัวใจสำคัญที่ทำให้ทีมรู้สึกปลอดภัยและอบอุ่นมาก ๆ 💗"
          : lvSupport.label === "ปานกลาง"
          ? "คุณช่วยเพื่อนเมื่อมีโอกาส แต่บางครั้งก็ต้องถอยกลับมาดูแลตัวเองก่อน ซึ่งเป็นเรื่องปกติและสำคัญเหมือนกัน ถ้าทีมแบ่งงานกันแฟร์ขึ้น คุณจะมีพลังไปสนับสนุนคนอื่นได้มากกว่านี้อีก ✨"
          : "คุณอาจยังไม่ค่อยเข้าไปช่วยหรือสนับสนุนคนอื่นเท่าไรนัก ซึ่งอาจมาจากการเหนื่อยล้า หรือยังไม่มั่นใจว่าจะช่วยยังไงดี การเริ่มจากประโยคง่าย ๆ อย่าง “มีอะไรให้ช่วยไหม” ก็ถือว่าเป็นการดูแลกันที่มีความหมายมากแล้ว 🤍";

      const avgPercent =
        ((totalScores.voice +
          totalScores.error +
          totalScores.inclusion +
          totalScores.support) /
          (maxScorePerDim * 4)) *
        100;

      if (avgPercent >= 75) {
        overallText.textContent =
          "โดยรวมแล้วบรรยากาศทีมที่คุณอยู่มีศักยภาพจะเป็นทีมที่ปลอดภัยทางจิตใจสูง ทั้งสไตล์ของคุณและท่าทีต่อเพื่อนช่วยให้ทีมกล้าพูด กล้าลอง และกล้าเติบโตไปด้วยกันต่อหน้าเพื่อน ๆ ถ้าคุณรักษาพลังนี้ไว้ พร้อมชวนคนอื่นช่วยกันดูแลบรรยากาศดี ๆ แบบนี้ ทีมของคุณจะยิ่งแข็งแรงมากขึ้นในอนาคตแน่นอน 🌈";
      } else if (avgPercent >= 50) {
        overallText.textContent =
          "ภาพรวมของคุณอยู่ในระดับกลาง ๆ แปลว่ามีทั้งช่วงที่รู้สึกปลอดภัยและช่วงที่ยังเกร็งอยู่เวลาอยู่ในทีม ซึ่งเป็นเรื่องปกติของหลาย ๆ กลุ่ม หากเริ่มจากการคุยกันตรง ๆ แบบสุภาพ เปิดพื้นที่ให้คนผิดพลาดได้ และถามไถ่ความรู้สึกกันบ่อยขึ้น บรรยากาศทีมของคุณจะค่อย ๆ อบอุ่นและน่าอยู่ขึ้นเรื่อย ๆ เลย 💬💛";
      } else {
        overallText.textContent =
          "ตอนนี้คุณอาจยังรู้สึกไม่ค่อยสบายใจเวลาอยู่ในทีม ทั้งการแสดงความคิดเห็นและการทำผิดพลาด นี่ไม่ใช่ความผิดของคุณเลย แต่เป็นสัญญาณว่าทีมอาจต้องช่วยกันสร้างพื้นที่ที่ปลอดภัยและอ่อนโยนต่อกันมากขึ้น ลองเริ่มจากการหาคนที่คุณไว้ใจได้สักหนึ่งคน แล้วค่อย ๆ แชร์ความรู้สึกเล็ก ๆ น้อย ๆ เกี่ยวกับทีม นั่นก็ถือว่าเป็นก้าวแรกที่กล้าหาญและมีความหมายมากแล้ว 💙";
      }
    }

    btnRestart.addEventListener("click", () => {
      showScreen(screenStart);
    });
  </script>
</body>
</html>
