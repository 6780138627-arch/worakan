<html lang="th">
<head>
  <meta charset="UTF-8" />
  <title>PSY SAFE QUEST - เกมสำรวจ Psychological Safety</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    * {
      box-sizing: border-box;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
      margin: 0;
      background: #f3f5fb;
      color: #1f2933;
    }

    .app-header {
      padding: 1.5rem 1.5rem 1rem;
      background: linear-gradient(120deg, #2563eb, #4f46e5);
      color: #f9fafb;
      text-align: center;
    }

    .app-header h1 {
      margin: 0 0 0.25rem;
      font-size: 1.7rem;
    }

    .app-header p {
      margin: 0;
      font-size: 0.95rem;
      opacity: 0.9;
    }

    .app-container {
      max-width: 900px;
      margin: 1.5rem auto 3rem;
      padding: 0 1rem;
    }

    .screen {
      display: none;
      background: #ffffff;
      border-radius: 18px;
      padding: 1.5rem 1.7rem 1.7rem;
      box-shadow: 0 18px 35px rgba(15, 23, 42, 0.08);
    }

    .screen.active {
      display: block;
    }

    h2 {
      margin-top: 0;
    }

    .hint-list {
      margin-top: 0.5rem;
      padding-left: 1.2rem;
      font-size: 0.95rem;
    }

    .input-label {
      display: block;
      margin: 1.5rem 0 0.8rem;
      font-size: 0.95rem;
    }

    input[type="text"] {
      width: 100%;
      padding: 0.6rem 0.8rem;
      border-radius: 10px;
      border: 1px solid #cbd5f5;
      font-size: 0.95rem;
    }

    .btn-primary,
    .btn-secondary {
      border: none;
      border-radius: 999px;
      padding: 0.55rem 1.4rem;
      font-size: 0.95rem;
      cursor: pointer;
      transition: transform 0.05s ease, box-shadow 0.1s ease, background 0.1s ease;
    }

    .btn-primary {
      background: #2563eb;
      color: white;
      box-shadow: 0 10px 20px rgba(37, 99, 235, 0.3);
    }

    .btn-secondary {
      background: #e5e7f5;
      color: #1f2933;
    }

    .btn-primary:hover,
    .btn-secondary:hover {
      transform: translateY(-1px);
    }

    .question-header {
      margin-bottom: 1rem;
    }

    #question-progress {
      font-size: 0.85rem;
      color: #6b7280;
    }

    .question-text {
      margin-top: 0.3rem;
    }

    .options-container {
      display: grid;
      gap: 0.8rem;
      margin: 1rem 0 1.2rem;
    }

    .option-card {
      padding: 0.8rem 0.9rem;
      border-radius: 12px;
      border: 1px solid #d1d5db;
      background: #f9fafb;
      cursor: pointer;
      font-size: 0.96rem;
      transition: background 0.1s ease, border-color 0.1s ease, transform 0.05s;
    }

    .option-card.selected {
      background: #2563eb;
      color: #f9fafb;
      border-color: #1d4ed8;
      transform: translateY(-1px);
    }

    .option-card small {
      display: block;
      margin-top: 0.25rem;
      opacity: 0.85;
      font-size: 0.8rem;
    }

    .reflection-box {
      margin-top: 0.5rem;
    }

    .reflection-box label {
      font-size: 0.9rem;
      display: block;
      margin-bottom: 0.25rem;
    }

    textarea {
      width: 100%;
      padding: 0.6rem 0.8rem;
      border-radius: 10px;
      border: 1px solid #cbd5f5;
      resize: vertical;
      font-size: 0.9rem;
    }

    .question-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 1.2rem;
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
      border-radius: 14px;
      background: #f3f4ff;
      padding: 0.9rem 1rem;
    }

    .result-card h3 {
      margin-top: 0;
      font-size: 1rem;
    }

    .result-card .score {
      font-weight: 600;
      margin-bottom: 0.3rem;
    }

    .overall-box {
      background: #eef2ff;
      border-radius: 14px;
      padding: 1rem 1.1rem;
      margin-bottom: 1rem;
    }

    .app-footer {
      text-align: center;
      font-size: 0.8rem;
      color: #6b7280;
      margin-bottom: 1rem;
    }
  </style>
</head>
<body>
  <header class="app-header">
    <h1>PSY SAFE QUEST</h1>
    <p>เกมกึ่งประเมินเพื่อสำรวจความปลอดภัยทางจิตใจในการทำงานเป็นทีมของนักเรียน</p>
  </header>

  <main class="app-container">

    <!-- หน้าต้อนรับ -->
    <section id="screen-start" class="screen active">
      <h2>ยินดีต้อนรับ 👋</h2>
      <p>
        คุณจะได้เล่นสถานการณ์จำลองเกี่ยวกับการทำงานเป็นทีม จำนวน 6 สถานการณ์  
        เลือกคำตอบที่ “ใกล้เคียงตัวคุณมากที่สุด”
      </p>
      <ul class="hint-list">
        <li>ไม่มีคำตอบถูกหรือผิด</li>
        <li>ตอบตามความรู้สึกจริงของคุณ</li>
        <li>ข้อมูลใช้เพื่อการเรียนรู้และพัฒนาทีม</li>
      </ul>

      <label class="input-label">
        ชื่อเล่นของคุณ:
        <input type="text" id="player-name" placeholder="เช่น แพรว, บอส, แทน" />
      </label>

      <button id="btn-start" class="btn-primary">เริ่มเล่นเกม</button>
    </section>

    <!-- หน้าคำถาม -->
    <section id="screen-question" class="screen">
      <div class="question-header">
        <span id="question-progress"></span>
        <h2 id="question-title"></h2>
        <p id="question-text" class="question-text"></p>
      </div>

      <div id="options-container" class="options-container">
        <!-- ตัวเลือกจะถูกใส่ด้วย JavaScript -->
      </div>

      <!-- ช่องสะท้อนคิดสั้น ๆ (optional) -->
      <div class="reflection-box">
        <label for="reflection-input">ถ้าเล่าเหตุการณ์คล้าย ๆ นี้ในชีวิตจริง คุณจะเล่ายังไง? (ไม่บังคับ)</label>
        <textarea id="reflection-input" rows="3" placeholder="พิมพ์ความคิด/ความรู้สึกของคุณ..."></textarea>
      </div>

      <div class="question-footer">
        <button id="btn-prev" class="btn-secondary">ย้อนกลับ</button>
        <button id="btn-next" class="btn-primary">ข้อต่อไป</button>
      </div>
    </section>

    <!-- หน้าผลลัพธ์ -->
    <section id="screen-result" class="screen">
      <h2>ผลลัพธ์ของคุณ 🎉</h2>
      <p id="result-intro"></p>

      <div class="result-grid">
        <div class="result-card">
          <h3>การกล้าแสดงความเห็น</h3>
          <p class="score" id="score-voice"></p>
          <p id="desc-voice"></p>
        </div>
        <div class="result-card">
          <h3>การยอมรับความผิดพลาด</h3>
          <p class="score" id="score-error"></p>
          <p id="desc-error"></p>
        </div>
        <div class="result-card">
          <h3>ความเป็นเจ้าของร่วมในทีม</h3>
          <p class="score" id="score-inclusion"></p>
          <p id="desc-inclusion"></p>
        </div>
        <div class="result-card">
          <h3>การสนับสนุนกันในทีม</h3>
          <p class="score" id="score-support"></p>
          <p id="desc-support"></p>
        </div>
      </div>

      <div class="overall-box">
        <h3>ภาพรวม Psychological Safety ของคุณ</h3>
        <p id="overall-text"></p>
      </div>

      <button id="btn-restart" class="btn-secondary">เล่นอีกครั้ง</button>
    </section>

  </main>

  <footer class="app-footer">
    <small>Prototype เพื่อการเรียนรู้ | สามารถต่อยอดเชื่อม AI วิเคราะห์ข้อความได้</small>
  </footer>

  <script>
    // ------------ ข้อมูลสถานการณ์ (แต่ละข้อมีมิติที่เน้น) ----------------

    const scenarios = [
      {
        id: 1,
        title: "สถานการณ์ที่ 1: เสนอไอเดียในที่ประชุม",
        text: "ในที่ประชุมสภานักเรียน เพื่อนส่วนใหญ่ดูเห็นด้วยกับแนวทางหนึ่งที่คุณไม่ค่อยมั่นใจ คุณมีไอเดียอีกแบบที่ต่างออกไป คุณจะทำอย่างไร?",
        options: [
          {
            text: "ยกมือเสนอไอเดียของตัวเองอย่างสุภาพ แม้จะต่างจากส่วนใหญ่",
            scores: { voice: 3, error: 2, inclusion: 2, support: 2 }
          },
          {
            text: "รอดูว่ามีใครเสนอไอเดียคล้าย ๆ คุณไหม ถ้ามีก็ค่อยเสริม",
            scores: { voice: 2, error: 2, inclusion: 2, support: 2 }
          },
          {
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
            text: "รีบบอกทีมและครูที่ปรึกษา ยอมรับว่าเป็นความผิดพลาดของตนเอง แล้วเสนอวิธีแก้",
            scores: { voice: 3, error: 3, inclusion: 2, support: 2 }
          },
          {
            text: "แก้ไขเงียบ ๆ แล้วส่งไฟล์ใหม่ โดยไม่เล่ารายละเอียดให้ทีมฟัง",
            scores: { voice: 2, error: 2, inclusion: 2, support: 1 }
          },
          {
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
            text: "ชวนคุยแบบส่วนตัว ถามว่าโอเคไหม และมีอะไรที่ทีมช่วยได้บ้าง",
            scores: { voice: 2, error: 2, inclusion: 3, support: 3 }
          },
          {
            text: "ปล่อยไปก่อน ถ้าเขามีปัญหาคงบอกเอง",
            scores: { voice: 2, error: 1, inclusion: 1, support: 1 }
          },
          {
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
            text: "ขอบคุณสำหรับความคิดเห็น แล้วถามต่อว่าควรปรับตรงไหนบ้าง",
            scores: { voice: 3, error: 3, inclusion: 2, support: 2 }
          },
          {
            text: "เงียบไป และพยายามเลี่ยงการเสนอไอเดียในครั้งต่อไป",
            scores: { voice: 1, error: 1, inclusion: 1, support: 1 }
          },
          {
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
            text: "เสนอให้ทีมคุยเรื่องแบ่งงานใหม่อย่างเปิดใจในที่ประชุมเล็ก ๆ",
            scores: { voice: 3, error: 2, inclusion: 3, support: 2 }
          },
          {
            text: "พยายามช่วยรับงานเพิ่มเอง เพื่อไม่ให้เรื่องยืดเยื้อ",
            scores: { voice: 2, error: 2, inclusion: 2, support: 3 }
          },
          {
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
            text: "ลองเสนอไอเดียใหม่ พร้อมยกตัวอย่างข้อดีข้อเสียให้ทีมพิจารณา",
            scores: { voice: 3, error: 2, inclusion: 2, support: 2 }
          },
          {
            text: "รอดูปีหน้าแล้วค่อยเสนอ เพราะกลัวว่าเปลี่ยนปีนี้จะวุ่นวาย",
            scores: { voice: 2, error: 2, inclusion: 2, support: 1 }
          },
          {
            text: "ไม่พูดอะไร เพราะคิดว่าทีมคงไม่อยากเปลี่ยนอยู่แล้ว",
            scores: { voice: 1, error: 1, inclusion: 1, support: 1 }
          }
        ]
      }
    ];

    // ------------ state ของเกม ----------------

    let currentIndex = 0;
    let selectedOptions = Array(scenarios.length).fill(null);
    let reflections = Array(scenarios.length).fill("");

    // คะแนนรวม
    const totalScores = {
      voice: 0,
      error: 0,
      inclusion: 0,
      support: 0
    };

    // ------------ อ้างอิง DOM ----------------

    const screenStart = document.getElementById("screen-start");
    const screenQuestion = document.getElementById("screen-question");
    const screenResult = document.getElementById("screen-result");

    const btnStart = document.getElementById("btn-start");
    const btnPrev = document.getElementById("btn-prev");
    const btnNext = document.getElementById("btn-next");
    const btnRestart = document.getElementById("btn-restart");

    const questionProgress = document.getElementById("question-progress");
    const questionTitle = document.getElementById("question-title");
    const questionText = document.getElementById("question-text");
    const optionsContainer = document.getElementById("options-container");
    const reflectionInput = document.getElementById("reflection-input");

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

    // ------------ ฟังก์ชันสลับหน้าจอ ----------------

    function showScreen(screen) {
      [screenStart, screenQuestion, screenResult].forEach((s) =>
        s.classList.remove("active")
      );
      screen.classList.add("active");
    }

    // ------------ เริ่มเกม ----------------

    btnStart.addEventListener("click", () => {
      const name = playerNameInput.value.trim();
      if (!name) {
        alert("กรุณากรอกชื่อเล่นก่อนเริ่มเกม 🙂");
        return;
      }
      currentIndex = 0;
      selectedOptions.fill(null);
      reflections.fill("");
      resetTotalScores();
      renderQuestion();
      showScreen(screenQuestion);
    });

    // ------------ แสดงคำถาม ----------------

    function renderQuestion() {
      const scenario = scenarios[currentIndex];
      questionProgress.textContent = `สถานการณ์ที่ ${currentIndex + 1} / ${
        scenarios.length
      }`;
      questionTitle.textContent = scenario.title;
      questionText.textContent = scenario.text;

      optionsContainer.innerHTML = "";
      scenario.options.forEach((opt, idx) => {
        const card = document.createElement("div");
        card.className = "option-card";
        card.textContent = opt.text;

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

      // ปุ่มย้อนกลับ
      btnPrev.disabled = currentIndex === 0;
      btnNext.textContent =
        currentIndex === scenarios.length - 1 ? "ดูผลลัพธ์" : "ข้อต่อไป";
    }

    // ------------ ปุ่มย้อนกลับ / ถัดไป ----------------

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
        alert("กรุณาเลือกคำตอบก่อนไปข้อต่อไปนะครับ 🙂");
        return;
      }

      if (currentIndex < scenarios.length - 1) {
        currentIndex++;
        renderQuestion();
      } else {
        // คำนวณคะแนนแล้วไปหน้าผลลัพธ์
        calculateScores();
        renderResult();
        showScreen(screenResult);
      }
    });

    function saveReflection() {
      reflections[currentIndex] = reflectionInput.value.trim();
    }

    // ------------ คำนวณคะแนน ----------------

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

    // ------------ แปลงคะแนนเป็นคำอธิบาย ----------------

    function levelText(score, maxScore) {
      const percent = (score / maxScore) * 100;
      if (percent >= 75) return { label: "สูง", color: "🟢" };
      if (percent >= 50) return { label: "ปานกลาง", color: "🟡" };
      return { label: "ต้องการดูแล", color: "🔴" };
    }

    function renderResult() {
      const name = playerNameInput.value.trim() || "คุณ";

      const maxScorePerDim = scenarios.length * 3; // 3 คือคะแนนสูงสุดต่อข้อ

      const lvVoice = levelText(totalScores.voice, maxScorePerDim);
      const lvError = levelText(totalScores.error, maxScorePerDim);
      const lvInclusion = levelText(totalScores.inclusion, maxScorePerDim);
      const lvSupport = levelText(totalScores.support, maxScorePerDim);

      resultIntro.textContent = `${name} ลองดูผลคะแนนแต่ละด้านด้านล่างนี้ แล้วใช้เป็นจุดเริ่มต้นในการพัฒนาตนเองและทีม 😊`;

      scoreVoice.textContent = `${totalScores.voice} / ${maxScorePerDim} (${lvVoice.color} ${lvVoice.label})`;
      scoreError.textContent = `${totalScores.error} / ${maxScorePerDim} (${lvError.color} ${lvError.label})`;
      scoreInclusion.textContent = `${totalScores.inclusion} / ${maxScorePerDim} (${lvInclusion.color} ${lvInclusion.label})`;
      scoreSupport.textContent = `${totalScores.support} / ${maxScorePerDim} (${lvSupport.color} ${lvSupport.label})`;

      descVoice.textContent =
        lvVoice.label === "สูง"
          ? "คุณค่อนข้างกล้าแสดงความเห็น และพร้อมเสนอไอเดียใหม่ ๆ เมื่อเห็นว่ามีประโยชน์ต่อทีม"
          : lvVoice.label === "ปานกลาง"
          ? "คุณกล้าแสดงความเห็นในบางสถานการณ์ แต่ยังมีบางครั้งที่เลือกเงียบเพื่อความสบายใจของตัวเองหรือทีม"
          : "คุณมักเก็บความคิดไว้ในใจ เพราะกังวลว่าพูดแล้วอาจทำให้คนอื่นไม่พอใจ หรือคิดว่าความเห็นของตัวเองไม่สำคัญมากนัก";

      descError.textContent =
        lvError.label === "สูง"
          ? "เมื่อเกิดความผิดพลาด คุณพร้อมยอมรับและมองเป็นโอกาสในการเรียนรู้ ซึ่งเป็นทักษะสำคัญของผู้นำ"
          : lvError.label === "ปานกลาง"
          ? "คุณพอรับมือกับความผิดพลาดได้ แต่บางครั้งยังรู้สึกกลัวหรือกังวลว่าคนอื่นจะมองอย่างไร"
          : "คุณอาจรู้สึกไม่สบายใจมากเมื่อทำผิด ทำให้พยายามหลีกเลี่ยงการพูดถึงความผิดพลาดของตนเอง";

      descInclusion.textContent =
        lvInclusion.label === "สูง"
          ? "คุณให้ความสำคัญกับการดึงทุกคนให้มีส่วนร่วม และมองว่าทีมที่ดีคือทีมที่ทุกคนรู้สึกเป็นเจ้าของร่วมกัน"
          : lvInclusion.label === "ปานกลาง"
          ? "คุณมีความพยายามทำให้ทีมรู้สึกเป็นเจ้าของร่วม แต่ยังมีบางครั้งที่ปล่อยผ่านสถานการณ์บางอย่าง"
          : "คุณอาจยังไม่ค่อยเข้าไปจัดการเมื่อเห็นเพื่อนบางคนถูกกันออกจากทีม หรือไม่ได้มีส่วนร่วมเท่าที่ควร";

      descSupport.textContent =
        lvSupport.label === "สูง"
          ? "คุณมักเป็นคนที่คอยสนับสนุนเพื่อนในทีม พร้อมช่วยเหลือเมื่อเห็นว่าคนอื่นลำบาก"
          : lvSupport.label === "ปานกลาง"
          ? "คุณช่วยเพื่อนเมื่อมีโอกาส แต่บางครั้งก็เลือกถอยมาโฟกัสที่งานของตัวเองก่อน"
          : "คุณอาจยังไม่ค่อยเข้าไปมีส่วนร่วมช่วยเหลือหรือสนับสนุนผู้อื่นในทีมเท่าไรนัก";

      const avgPercent =
        ((totalScores.voice +
          totalScores.error +
          totalScores.inclusion +
          totalScores.support) /
          (maxScorePerDim * 4)) *
        100;

      if (avgPercent >= 75) {
        overallText.textContent =
          "โดยรวมแล้วทีมที่คุณอยู่มีศักยภาพจะเป็นทีมที่ปลอดภัยทางจิตใจสูง หากคุณรักษาน้ำเสียงที่เปิดรับและชวนคนอื่นมีส่วนร่วมต่อไป คุณสามารถช่วยเป็นแกนนำสร้างบรรยากาศดี ๆ ในทีมได้เลย!";
      } else if (avgPercent >= 50) {
        overallText.textContent =
          "ภาพรวมของคุณอยู่ในระดับปานกลาง แปลว่าคุณมีทั้งช่วงเวลาที่รู้สึกปลอดภัยและไม่ค่อยปลอดภัยในทีม การฝึกลองพูดมากขึ้น ถามเพื่อนมากขึ้น และเปิดพื้นที่ให้คนอื่นผิดพลาดได้ จะช่วยยกระดับบรรยากาศให้ดีขึ้นได้มาก";
      } else {
        overallText.textContent =
          "ตอนนี้คุณอาจยังรู้สึกไม่ค่อยปลอดภัยนักในการแสดงความคิดเห็นหรือทำผิดพลาดในทีม นี่ไม่ใช่ข้อเสียของคุณ แต่เป็นสัญญาณว่าทีมอาจยังต้องสร้างบรรยากาศที่ปลอดภัยมากกว่านี้ ลองค่อย ๆ หาคนที่ไว้ใจได้คุย และเริ่มจากการแบ่งปันความคิดเล็ก ๆ ก่อนก็เป็นจุดเริ่มต้นที่ดี";
      }
    }

    // ------------ เริ่มใหม่ ----------------

    btnRestart.addEventListener("click", () => {
      showScreen(screenStart);
    });

    // หมายเหตุ: ถ้าจะเชื่อม AI API มาวิเคราะห์ข้อความ reflection
    // สามารถเพิ่มฟังก์ชัน fetch ไปหา backend หรือ OpenAI API ตรงนี้ได้ในอนาคต
  </script>
</body>
</html>
