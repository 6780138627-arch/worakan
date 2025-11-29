<html lang="th">
<head>
  <meta charset="UTF-8" />
  <title>PSY SAFE QUEST - เกมสำรวจ Psychological Safety</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --bg-gradient: radial-gradient(circle at top left, #fee2e2, #e0f2fe, #ede9fe);
      --primary: #6366f1;
      --primary-soft: #eef2ff;
      --accent: #fb7185;
      --accent-soft: #ffe4e6;
      --card-bg: #ffffff;
      --text-main: #111827;
      --text-soft: #6b7280;
      --shadow-soft: 0 18px 35px rgba(15, 23, 42, 0.08);
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
      max-width: 900px;
      margin: 0 auto;
      background: rgba(255, 255, 255, 0.9);
      border-radius: 999px;
      padding: 0.8rem 1.5rem;
      display: flex;
      flex-direction: column;
      gap: 0.2rem;
      box-shadow: 0 12px 25px rgba(15, 23, 42, 0.1);
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
      gap: 0.6rem;
      justify-content: center;
    }

    .brand-badge {
      width: 40px;
      height: 40px;
      border-radius: 18px;
      background: conic-gradient(from 160deg, #fb7185, #6366f1, #22c55e, #fb7185);
      display: flex;
      align-items: center;
      justify-content: center;
      color: #f9fafb;
      font-weight: 700;
      font-size: 1.1rem;
      box-shadow: 0 8px 18px rgba(15, 23, 42, 0.18);
    }

    .brand-text h1 {
      margin: 0;
      font-size: 1.4rem;
      letter-spacing: 0.02em;
    }

    .brand-text span {
      font-size: 0.85rem;
      color: var(--text-soft);
    }

    .tagline {
      font-size: 0.85rem;
      color: var(--text-soft);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.4rem;
      margin-top: 0.3rem;
      flex-wrap: wrap;
    }

    .pill {
      padding: 0.18rem 0.7rem;
      border-radius: 999px;
      background: #ecfeff;
      color: #0f766e;
      font-size: 0.78rem;
      font-weight: 500;
    }

    .app-container {
      flex: 1;
      max-width: 900px;
      width: 100%;
      margin: 0 auto 2.2rem;
      padding: 0 1rem;
      display: flex;
      justify-content: center;
      align-items: flex-start;
    }

    .screen {
      display: none;
      background: var(--card-bg);
      border-radius: var(--radius-xl);
      padding: 1.6rem 1.7rem 1.8rem;
      box-shadow: var(--shadow-soft);
      width: 100%;
      margin-top: 0.5rem;
      animation: fadeInUp 0.35s ease-out;
      position: relative;
      overflow: hidden;
    }

    .screen::before {
      content: "";
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at top right, rgba(129, 140, 248, 0.18), transparent 55%);
      opacity: 0.7;
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
        transform: translateY(10px);
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
      content: "✨";
      font-size: 1.2rem;
    }

    .hint-list {
      margin-top: 0.5rem;
      padding-left: 1.2rem;
      font-size: 0.95rem;
      color: var(--text-soft);
    }

    .hint-list li {
      margin-bottom: 0.15rem;
    }

    .input-label {
      display: block;
      margin: 1.5rem 0 0.8rem;
      font-size: 0.95rem;
      font-weight: 500;
    }

    input[type="text"] {
      width: 100%;
      padding: 0.7rem 0.9rem;
      border-radius: 12px;
      border: 1px solid #dbe2ff;
      font-size: 0.95rem;
      background: #f9fafb;
      transition: border-color 0.15s ease, box-shadow 0.15s ease, background 0.15s;
    }

    input[type="text"]:focus {
      outline: none;
      border-color: var(--primary);
      background: #ffffff;
      box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.2);
    }

    .btn-primary,
    .btn-secondary {
      border: none;
      border-radius: 999px;
      padding: 0.65rem 1.6rem;
      font-size: 0.95rem;
      cursor: pointer;
      transition: transform 0.05s ease, box-shadow 0.1s ease, background 0.15s;
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      font-weight: 500;
    }

    .btn-primary {
      background: linear-gradient(120deg, #6366f1, #ec4899);
      color: white;
      box-shadow: 0 12px 25px rgba(129, 140, 248, 0.6);
    }

    .btn-secondary {
      background: rgba(248, 250, 252, 0.9);
      color: #111827;
      border: 1px solid #e5e7eb;
    }

    .btn-primary:hover,
    .btn-secondary:hover {
      transform: translateY(-1px);
      box-shadow: 0 14px 30px rgba(15, 23, 42, 0.12);
    }

    .btn-primary:active,
    .btn-secondary:active {
      transform: translateY(0);
      box-shadow: none;
    }

    .btn-primary:disabled,
    .btn-secondary:disabled {
      opacity: 0.5;
      cursor: default;
      box-shadow: none;
      transform: none;
    }

    .question-header {
      margin-bottom: 1rem;
    }

    #question-progress {
      font-size: 0.85rem;
      color: var(--text-soft);
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 0.5rem;
      flex-wrap: wrap;
    }

    #question-progress span {
      font-weight: 500;
      color: #4b5563;
    }

    .progress-bar {
      flex: 1;
      height: 7px;
      border-radius: 999px;
      background: #e5e7eb;
      overflow: hidden;
    }

    .progress-bar-inner {
      height: 100%;
      width: 0;
      background: linear-gradient(90deg, #6366f1, #22c55e);
      transition: width 0.25s ease;
    }

    .question-text {
      margin-top: 0.5rem;
      font-size: 1rem;
    }

    .options-container {
      display: grid;
      gap: 0.9rem;
      margin: 1.1rem 0 1.3rem;
    }

    .option-card {
      padding: 0.9rem 1rem;
      border-radius: 15px;
      border: 1px solid #e5e7eb;
      background: #f9fafb;
      cursor: pointer;
      font-size: 0.96rem;
      transition: background 0.1s ease, border-color 0.1s ease, transform 0.05s,
        box-shadow 0.1s ease;
      display: flex;
      gap: 0.75rem;
      align-items: flex-start;
    }

    .option-icon {
      width: 28px;
      height: 28px;
      border-radius: 999px;
      background: #e0f2fe;
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
      background: #eef2ff;
      border-color: #c7d2fe;
      transform: translateY(-1px);
      box-shadow: 0 10px 20px rgba(148, 163, 184, 0.35);
    }

    .option-card.selected {
      background: radial-gradient(circle at top left, #6366f1, #ec4899);
      color: #f9fafb;
      border-color: transparent;
      box-shadow: 0 16px 32px rgba(129, 140, 248, 0.65);
    }

    .option-card.selected .option-icon {
      background: rgba(248, 250, 252, 0.15);
    }

    .reflection-box {
      margin-top: 0.5rem;
      padding: 0.85rem 0.9rem;
      border-radius: 14px;
      background: rgba(239, 246, 255, 0.8);
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
      padding: 0.55rem 0.75rem;
      border-radius: 10px;
      border: 1px solid #dbeafe;
      resize: vertical;
      font-size: 0.9rem;
      background: #ffffff;
      min-height: 60px;
    }

    textarea:focus {
      outline: none;
      border-color: #3b82f6;
      box-shadow: 0 0 0 2px rgba(59, 130, 246, 0.35);
    }

    .question-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 1.3rem;
      gap: 0.6rem;
    }

    .question-footer span {
      font-size: 0.82rem;
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
      border-radius: 16px;
      background: linear-gradient(135deg, #eef2ff, #fef2f2);
      padding: 0.9rem 1rem;
      border: 1px solid rgba(209, 213, 219, 0.8);
      box-shadow: 0 10px 20px rgba(148, 163, 184, 0.25);
    }

    .result-card h3 {
      margin-top: 0;
      font-size: 0.98rem;
      display: flex;
      align-items: center;
      gap: 0.3rem;
    }

    .result-card .score {
      font-weight: 600;
      margin-bottom: 0.3rem;
    }

    .overall-box {
      background: linear-gradient(120deg, #ecfeff, #eef2ff);
      border-radius: 18px;
      padding: 1rem 1.1rem;
      margin-bottom: 1rem;
      border: 1px solid #bae6fd;
    }

    .overall-box h3 {
      margin-top: 0;
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
        <div class="brand-badge">Q</div>
        <div class="brand-text">
          <h1>PSY SAFE QUEST</h1>
          <span>ชวนสำรวจความรู้สึกในทีม แบบเบา ๆ แต่มีความหมาย 💫</span>
        </div>
      </div>
      <div class="tagline">
        <span>ตอบแบบสบายใจ ไม่มีคำตอบถูกหรือผิด</span>
        <span class="pill">สำหรับนักเรียน & ทีมสภานักเรียน</span>
      </div>
    </div>
  </header>

  <main class="app-container">

    <!-- หน้าต้อนรับ -->
    <section id="screen-start" class="screen active">
      <h2>ยินดีต้อนรับ 👋</h2>
      <p>
        เกมนี้จะมีสถานการณ์เกี่ยวกับการทำงานเป็นทีมทั้งหมด <strong>6 สถานการณ์</strong><br />
        แค่เลือกคำตอบที่ “ใกล้กับตัวตนของคุณที่สุด” แล้วเราจะช่วยสรุปภาพรวมให้ว่า<br />
        คุณรู้สึกปลอดภัยแค่ไหนเวลาอยู่ในทีม 😊
      </p>
      <ul class="hint-list">
        <li>ไม่มีคำตอบถูกหรือผิด ทุกคำตอบคือ “ตัวคุณ”</li>
        <li>ข้อมูลใช้เพื่อสะท้อนคิดและพัฒนาทีม ไม่ได้ใช้ตัดสินใคร</li>
        <li>ถ้าอยากเล่าประสบการณ์เพิ่ม สามารถพิมพ์ในช่องสะท้อนคิดได้</li>
      </ul>

      <label class="input-label">
        ชื่อเล่นของคุณ (ไว้เรียกแบบกันเองในผลลัพธ์):
        <input type="text" id="player-name" placeholder="เช่น แพรว, บอส, แทน" />
      </label>

      <button id="btn-start" class="btn-primary">
        <span>เริ่มเล่นเกม</span> <span>▶</span>
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
        <label for="reflection-input">ถ้าเล่าเหตุการณ์คล้าย ๆ นี้ในชีวิตจริง คุณจะเล่ายังไง? (ไม่บังคับ)</label>
        <textarea id="reflection-input" rows="3" placeholder="พิมพ์ความคิด/ความรู้สึกเพิ่มเติมได้ที่นี่..."></textarea>
      </div>

      <div class="question-footer">
        <button id="btn-prev" class="btn-secondary">
          ◀ ย้อนกลับ
        </button>
        <div>
          <span id="helper-text">เลือกคำตอบแล้วกด “ข้อต่อไป”</span>
          <button id="btn-next" class="btn-primary">
            ข้อต่อไป ▶
          </button>
        </div>
      </div>
    </section>

    <!-- หน้าผลลัพธ์ -->
    <section id="screen-result" class="screen">
      <h2>ผลลัพธ์ของคุณ 🎉</h2>
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
        <h3>ภาพรวม Psychological Safety ของคุณ</h3>
        <p id="overall-text"></p>
      </div>

      <button id="btn-restart" class="btn-secondary">
        🔁 เล่นอีกครั้ง หรือให้เพื่อนลองเล่นดู
      </button>
    </section>

  </main>

  <footer class="app-footer">
    <small>Prototype เพื่อการเรียนรู้ | สามารถต่อยอดเชื่อม AI วิเคราะห์ข้อความได้ในอนาคต 💡</small>
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
      const progressPercent = ((currentIndex) / scenarios.length) * 100;
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
        currentIndex === scenarios.length - 1 ? "ดูผลลัพธ์ 🎯" : "ข้อต่อไป ▶";

      helperText.textContent =
        currentIndex === scenarios.length - 1
          ? "ข้อนี้ข้อสุดท้ายแล้ว เลือกคำตอบแล้วกด “ดูผลลัพธ์” ได้เลย"
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

      resultIntro.textContent = `${name} นี่คือภาพรวมสไตล์การทำงานในทีมของคุณ ลองอ่านแบบไม่ตัดสินตัวเอง แล้วค่อย ๆ ใช้มันเป็นไอเดียในการพัฒนาตัวเองและทีมไปด้วยกัน 😊`;

      scoreVoice.textContent = `${totalScores.voice} / ${maxScorePerDim} (${lvVoice.color} ${lvVoice.label})`;
      scoreError.textContent = `${totalScores.error} / ${maxScorePerDim} (${lvError.color} ${lvError.label})`;
      scoreInclusion.textContent = `${totalScores.inclusion} / ${maxScorePerDim} (${lvInclusion.color} ${lvInclusion.label})`;
      scoreSupport.textContent = `${totalScores.support} / ${maxScorePerDim} (${lvSupport.color} ${lvSupport.label})`;

      descVoice.textContent =
        lvVoice.label === "สูง"
          ? "คุณค่อนข้างกล้าแสดงความเห็น และพร้อมเสนอไอเดียใหม่ ๆ เมื่อเห็นว่ามีประโยชน์ต่อทีม เป็นพลังสำคัญที่ช่วยให้ทีมไม่หยุดอยู่กับที่"
          : lvVoice.label === "ปานกลาง"
          ? "คุณกล้าแสดงความเห็นในบางสถานการณ์ โดยเฉพาะเมื่อรู้สึกว่าบรรยากาศปลอดภัย แปลว่าถ้าทีมช่วยกันสร้างบรรยากาศดี ๆ คุณจะกล้าเปล่งเสียงของตัวเองได้มากขึ้น"
          : "คุณมักเก็บความคิดไว้ในใจ เพราะกังวลว่าพูดแล้วอาจทำให้คนอื่นไม่สบายใจ หรือกลัวถูกมองแปลกไป สิ่งนี้เข้าใจได้มาก แต่อาจทำให้ทีมพลาดไอเดียดี ๆ จากคุณไป";

      descError.textContent =
        lvError.label === "สูง"
          ? "เมื่อเกิดความผิดพลาด คุณพร้อมยอมรับและมองเป็นโอกาสเรียนรู้ ซึ่งเป็นทักษะสำคัญของผู้นำและคนทำงานมืออาชีพในอนาคต"
          : lvError.label === "ปานกลาง"
          ? "คุณพอรับมือกับความผิดพลาดได้ แต่บางครั้งยังรู้สึกกลัวสายตาคนอื่น สิ่งนี้เป็นเรื่องธรรมดา แต่หากทีมช่วยกันยอมรับความผิดพลาดได้มากขึ้น คุณจะสบายใจกับการลองผิดลองถูกมากขึ้น"
          : "คุณอาจรู้สึกเครียดเมื่อทำผิด ทำให้พยายามหลีกเลี่ยงการพูดถึงความผิดพลาดของตัวเอง นี่ไม่ใช่ข้อด้อยของคุณ แต่สะท้อนว่าทีมอาจต้องสร้างพื้นที่ที่ปลอดภัยต่อการผิดพลาดให้มากกว่านี้";

      descInclusion.textContent =
        lvInclusion.label === "สูง"
          ? "คุณให้ความสำคัญกับการดึงทุกคนให้มีส่วนร่วม และมองว่าทีมที่ดีคือทีมที่ทุกคนรู้สึกเป็นเจ้าของร่วมกัน พลังแบบนี้ช่วยให้เพื่อนหลายคนรู้สึกกล้าเข้ามามีส่วนร่วมมากขึ้น"
          : lvInclusion.label === "ปานกลาง"
          ? "คุณมองเห็นความสำคัญของการมีส่วนร่วม แต่บางครั้งอาจยังไม่ค่อยกล้าเข้าไปชวนหรือสะกิดเพื่อนที่เงียบเท่าไร หากลองเริ่มจากคำถามง่าย ๆ เช่น “โอเคไหม” หรือ “คิดว่ายังไงบ้าง” ก็จะช่วยให้บรรยากาศดีขึ้นได้มาก"
          : "คุณอาจยังไม่ค่อยเข้าไปจัดการเมื่อเห็นเพื่อนบางคนถูกกันออกจากทีม หรือไม่ได้มีส่วนร่วม สิ่งนี้เข้าใจได้ เพราะหลายครั้งก็กลัวสถานการณ์จะ ‘ดราม่า’ แต่ถ้าคุณเริ่มต้นจากการรับฟังเพื่อนเงียบ ๆ แค่คนเดียว ก็ถือว่าเป็นก้าวสำคัญแล้ว";

      descSupport.textContent =
        lvSupport.label === "สูง"
          ? "คุณมักเป็นคนที่คอยสนับสนุนเพื่อน พร้อมช่วยเหลือเมื่อเห็นว่าคนอื่นลำบาก คนแบบคุณคือหัวใจสำคัญที่ทำให้ทีมรู้สึกอบอุ่นและไว้ใจกันได้"
          : lvSupport.label === "ปานกลาง"
          ? "คุณช่วยเพื่อนเมื่อมีโอกาส แต่บางครั้งก็ต้องถอยกลับมาดูแลตัวเองก่อน ซึ่งเป็นเรื่องสมดุลที่ดี หากทีมแบ่งงานกันแฟร์ขึ้น คุณจะยิ่งมีพลังช่วยคนอื่นได้มากกว่านี้"
          : "คุณอาจยังไม่ค่อยเข้าไปช่วยหรือสนับสนุนผู้อื่นเท่าไรนัก ซึ่งอาจมาจากความเหนื่อยล้าของตนเอง หรือยังไม่มั่นใจว่าควรช่วยอย่างไร การเริ่มจากคำถามง่าย ๆ เช่น “มีอะไรให้ช่วยไหม” ก็เป็นจุดเริ่มต้นที่ดีมากแล้ว";

      const avgPercent =
        ((totalScores.voice +
          totalScores.error +
          totalScores.inclusion +
          totalScores.support) /
          (maxScorePerDim * 4)) *
        100;

      if (avgPercent >= 75) {
        overallText.textContent =
          "โดยรวมแล้วคุณมีแนวโน้มอยู่ในทีมที่สามารถเป็นพื้นที่ปลอดภัยทางจิตใจได้สูง ทั้งสไตล์ของคุณและท่าทีต่อเพื่อนช่วยให้ทีมกล้าพูด กล้าลอง และกล้าผิดพลาดต่อหน้ากันต่อไป หากคุณรักษาพลังนี้ไว้ พร้อมชวนเพื่อนคนอื่นร่วมสร้างบรรยากาศดี ๆ จะทำให้ทีมของคุณแข็งแรงมากในระยะยาว 💪💜";
      } else if (avgPercent >= 50) {
        overallText.textContent =
          "ภาพรวมของคุณอยู่ในระดับกลาง ๆ แปลว่ามีทั้งช่วงที่รู้สึกปลอดภัย และช่วงที่ยังเกร็งอยู่ในทีม สิ่งนี้เป็นเรื่องปกติมากในหลาย ๆ กลุ่ม หากเริ่มจากการพูดตรง ๆ อย่างสุภาพมากขึ้น เปิดพื้นที่ให้เพื่อนผิดพลาดได้ และถามไถ่ความรู้สึกกันบ่อยขึ้น บรรยากาศของทีมจะนุ่มนวลและปลอดภัยขึ้นเรื่อย ๆ 🌱";
      } else {
        overallText.textContent =
          "ตอนนี้คุณอาจยังรู้สึกไม่ค่อยปลอดภัยเวลาอยู่ในทีม ทั้งการแสดงความคิดเห็นและการทำผิดพลาด นี่ไม่ใช่ความผิดของคุณเลย แต่เป็นสัญญาณว่าทีมอาจยังต้องช่วยกันสร้างพื้นที่ปลอดภัยให้กันมากขึ้น ลองเริ่มจากการหาคนที่คุณไว้ใจได้สักหนึ่งคน แล้วค่อย ๆ เปิดใจเล่าเรื่องเล็ก ๆ ในทีมให้เขาฟัง นั่นก็ถือว่าเป็นก้าวแรกที่มีคุณค่ามากแล้ว 💙";
      }
    }

    btnRestart.addEventListener("click", () => {
      showScreen(screenStart);
    });
  </script>
</body>
</html>
