<html lang="th">
<head>
  <meta charset="UTF-8" />
  <title>PSY SAFE QUEST - เกมสำรวจ Psychological Safety</title>
  <link rel="stylesheet" href="style.css" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
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

  <script src="script.js"></script>
</body>
</html>

