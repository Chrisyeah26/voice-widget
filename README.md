<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>ABC Heating & Cooling</title>
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet"/>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'DM Sans', sans-serif;
      background: #f0f4f8;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .demo-page { text-align: center; color: #334155; }
    .demo-page h1 { font-size: 28px; font-weight: 600; margin-bottom: 8px; }
    .demo-page p  { font-size: 15px; color: #64748b; }

    #vc-launcher {
      position: fixed;
      bottom: 28px;
      right: 28px;
      background: #1d4ed8;
      color: #fff;
      border: none;
      border-radius: 50px;
      padding: 14px 22px;
      font-size: 14px;
      font-weight: 600;
      font-family: 'DM Sans', sans-serif;
      cursor: pointer;
      box-shadow: 0 4px 18px rgba(29,78,216,0.4);
      z-index: 9999;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: transform .15s, box-shadow .15s;
    }
    #vc-launcher:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 22px rgba(29,78,216,0.5);
    }

    #vc-modal {
      display: none;
      position: fixed;
      bottom: 90px;
      right: 28px;
      width: 330px;
      background: #fff;
      border-radius: 18px;
      box-shadow: 0 12px 40px rgba(0,0,0,0.14);
      padding: 24px;
      z-index: 9999;
      font-family: 'DM Sans', sans-serif;
      animation: slideUp .2s ease;
    }
    @keyframes slideUp {
      from { opacity: 0; transform: translateY(12px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    #vc-modal.open { display: block; }

    .vc-header {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-bottom: 16px;
    }
    .vc-header h3 { font-size: 16px; font-weight: 600; color: #0f172a; }
    .vc-header p  { font-size: 12px; color: #64748b; margin-top: 2px; }
    #vc-close {
      background: none;
      border: none;
      font-size: 18px;
      cursor: pointer;
      color: #94a3b8;
      line-height: 1;
      padding: 2px 4px;
    }
    #vc-close:hover { color: #334155; }

    .vc-input {
      width: 100%;
      padding: 10px 13px;
      border: 1.5px solid #e2e8f0;
      border-radius: 10px;
      font-size: 13px;
      font-family: 'DM Sans', sans-serif;
      color: #0f172a;
      background: #f8fafc;
      margin-bottom: 10px;
      outline: none;
      transition: border-color .15s;
    }
    .vc-input:focus { border-color: #1d4ed8; background: #fff; }

    #vc-mic-btn {
      width: 100%;
      padding: 11px;
      background: #eff6ff;
      border: 2px dashed #93c5fd;
      border-radius: 10px;
      color: #1d4ed8;
      font-size: 13px;
      font-family: 'DM Sans', sans-serif;
      font-weight: 500;
      cursor: pointer;
      margin-bottom: 10px;
      transition: all .15s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 7px;
    }
    #vc-mic-btn:hover { background: #dbeafe; }
    #vc-mic-btn.recording {
      background: #fef2f2;
      border-color: #fca5a5;
      color: #dc2626;
      animation: pulse 1.2s infinite;
    }
    @keyframes pulse {
      0%,100% { box-shadow: 0 0 0 0 rgba(220,38,38,0.2); }
      50%      { box-shadow: 0 0 0 6px rgba(220,38,38,0); }
    }

    #vc-submit {
      width: 100%;
      padding: 12px;
      background: #1d4ed8;
      color: #fff;
      border: none;
      border-radius: 10px;
      font-size: 14px;
      font-family: 'DM Sans', sans-serif;
      font-weight: 600;
      cursor: pointer;
      transition: background .15s, transform .1s;
    }
    #vc-submit:hover  { background: #1e40af; }
    #vc-submit:active { transform: scale(.98); }
    #vc-submit:disabled { background: #93c5fd; cursor: not-allowed; }

    #vc-status {
      font-size: 12px;
      text-align: center;
      margin-top: 10px;
      min-height: 18px;
      font-weight: 500;
    }

    #vc-success {
      display: none;
      text-align: center;
      padding: 10px 0 4px;
    }
    #vc-success .checkmark { font-size: 36px; margin-bottom: 8px; }
    #vc-success h4 { font-size: 15px; font-weight: 600; color: #0f172a; margin-bottom: 4px; }
    #vc-success p  { font-size: 12px; color: #64748b; line-height: 1.5; }
  </style>
</head>
<body>

  <div class="demo-page">
    <h1>🏠 ABC Heating & Cooling</h1>
    <p>Your trusted HVAC, Electrical & Plumbing experts</p>
    <br/>
    <p style="font-size:13px; color:#94a3b8;">👉 Click the blue button in the bottom-right corner to test the widget</p>
  </div>

  <button id="vc-launcher">🎙️ Report an Issue</button>

  <div id="vc-modal">
    <div class="vc-header">
      <div>
        <h3>Report Your Issue</h3>
        <p>We'll call you back within 2 hours</p>
      </div>
      <button id="vc-close">✕</button>
    </div>

    <div id="vc-form">
      <input id="vc-name"  class="vc-input" type="text" placeholder="Your Name" />
      <input id="vc-phone" class="vc-input" type="tel"  placeholder="Your Phone Number" />
      <button id="vc-mic-btn">🎤 Tap to Speak Your Issue</button>
      <textarea id="vc-issue" class="vc-input" rows="3"
        placeholder="Or type your issue here..."></textarea>
      <select id="vc-type" class="vc-input">
        <option value="">Select Issue Type</option>
        <option value="HVAC">HVAC / Air Conditioning</option>
        <option value="Heating">Heating / Furnace</option>
        <option value="Electrical">Electrical</option>
        <option value="Plumbing">Plumbing</option>
        <option value="Other">Other</option>
      </select>
      <button id="vc-submit">Submit Issue →</button>
      <div id="vc-status"></div>
    </div>

    <div id="vc-success">
      <div class="checkmark">✅</div>
      <h4>Request Received!</h4>
      <p>We've notified the team and will call you back shortly.</p>
    </div>
  </div>

  <script>
    const WEBHOOK_URL = "PASTE_YOUR_MAKE_WEBHOOK_URL_HERE";
    const BUSINESS_NAME = "ABC Heating & Cooling";

    const modal    = document.getElementById("vc-modal");
    const launcher = document.getElementById("vc-launcher");
    const closeBtn = document.getElementById("vc-close");

    launcher.addEventListener("click", () => modal.classList.toggle("open"));
    closeBtn.addEventListener("click", () => modal.classList.remove("open"));

    const micBtn   = document.getElementById("vc-mic-btn");
    const issueBox = document.getElementById("vc-issue");
    let   isRecording = false;
    let   recognition = null;

    const SpeechAPI = window.SpeechRecognition || window.webkitSpeechRecognition;

    if (SpeechAPI) {
      recognition = new SpeechAPI();
      recognition.continuous      = false;
      recognition.interimResults  = false;
      recognition.lang            = "en-US";

      recognition.onresult = (e) => {
        issueBox.value = e.results[0][0].transcript;
        stopRecording();
      };
      recognition.onerror = () => stopRecording();
      recognition.onend   = () => stopRecording();

      micBtn.addEventListener("click", () => {
        if (isRecording) {
          recognition.stop();
        } else {
          issueBox.value = "";
          recognition.start();
          isRecording = true;
          micBtn.textContent = "🔴 Listening... Tap to Stop";
          micBtn.classList.add("recording");
        }
      });
    } else {
      micBtn.style.display = "none";
      issueBox.placeholder = "Type your issue here...";
    }

    function stopRecording() {
      isRecording = false;
      micBtn.textContent = "🎤 Tap to Speak Your Issue";
      micBtn.classList.remove("recording");
    }

    const submitBtn = document.getElementById("vc-submit");
    const statusEl  = document.getElementById("vc-status");
    const formEl    = document.getElementById("vc-form");
    const successEl = document.getElementById("vc-success");

    submitBtn.addEventListener("click", async () => {
      const name  = document.getElementById("vc-name").value.trim();
      const phone = document.getElementById("vc-phone").value.trim();
      const issue = issueBox.value.trim();
      const type  = document.getElementById("vc-type").value;

      if (!name || !phone || !issue) {
        statusEl.style.color = "#dc2626";
        statusEl.textContent  = "⚠️ Please fill in your name, phone, and issue.";
        return;
      }

      submitBtn.disabled    = true;
      statusEl.style.color  = "#64748b";
      statusEl.textContent  = "Sending...";

      const payload = {
        name,
        phone,
        issue,
        issue_type:   type || "Not specified",
        business:     BUSINESS_NAME,
        submitted_at: new Date().toLocaleString()
      };

      if (WEBHOOK_URL === "PASTE_YOUR_MAKE_WEBHOOK_URL_HERE") {
        setTimeout(() => showSuccess(), 800);
        return;
      }

      try {
        await fetch(WEBHOOK_URL, {
          method:  "POST",
          headers: { "Content-Type": "application/json" },
          body:    JSON.stringify(payload)
        });
        showSuccess();
      } catch (err) {
        statusEl.style.color = "#dc2626";
        statusEl.textContent  = "❌ Something went wrong. Please call us directly.";
        submitBtn.disabled    = false;
      }
    });

    function showSuccess() {
      formEl.style.display    = "none";
      successEl.style.display = "block";
      setTimeout(() => {
        modal.classList.remove("open");
        formEl.style.display    = "block";
        successEl.style.display = "none";
        submitBtn.disabled      = false;
        statusEl.textContent    = "";
        document.getElementById("vc-name").value  = "";
        document.getElementById("vc-phone").value = "";
        issueBox.value = "";
        document.getElementById("vc-type").value  = "";
      }, 4000);
    }
  </script>

</body>
</html>
