<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Brain & Mind | Solving Equations with Variables on Both Sides</title>
  
  <!-- MathJax Configuration for Clean LaTeX Rendering -->
  <script>
    window.MathJax = {
      tex: {
        inlineMath: [['\\(', '\\)'], ['$', '$']],
        displayMath: [['\\[', '\\]'], ['$$', '$$']],
        processEscapes: true
      },
      options: {
        skipHtmlTags: ['script', 'noscript', 'style', 'textarea', 'pre', 'code']
      },
      startup: {
        pageReady: () => MathJax.startup.defaultPageReady()
      }
    };
  </script>
  <script type="text/javascript" id="MathJax-script" async
    src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  </script>

  <style>
    :root {
      --primary-blue: #0284c7;
      --primary-dark: #0c4a6e;
      --accent-blue: #0ea5e9;
      --light-blue-bg: #f0f9ff;
      --light-blue-card: #f8fafc;
      --blue-border: #7dd3fc;
      --blue-border-soft: #bae6fd;
      --card-white: #ffffff;
      --correct-green: #059669;
      --correct-green-light: #d1fae5;
      --incorrect-red: #dc2626;
      --incorrect-red-light: #fee2e2;
      --brand-gold: #f59e0b;
      --brand-gold-dark: #d97706;
      --text-main: #0f172a;
      --text-muted: #475569;
      --radius-sm: 8px;
      --radius-md: 14px;
      --radius-lg: 20px;
      --shadow-sm: 0 1px 3px rgba(2, 132, 199, 0.08);
      --shadow-md: 0 4px 8px -1px rgba(2, 132, 199, 0.12);
      --shadow-lg: 0 12px 24px -4px rgba(12, 74, 110, 0.15);
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, Roboto, sans-serif;
      background: linear-gradient(180deg, #f0f9ff 0%, #ffffff 320px, #f0f9ff 100%);
      color: var(--text-main);
      line-height: 1.6;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    /* Header */
    header {
      background: linear-gradient(135deg, var(--primary-dark) 0%, #0369a1 60%, var(--primary-blue) 100%);
      color: #ffffff; padding: 0.85rem 1.75rem; box-shadow: var(--shadow-md); position: sticky; top: 0; z-index: 100;
    }
    .header-container {
      max-width: 1440px; margin: 0 auto; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1rem;
    }
    .brand-group { display: flex; align-items: center; gap: 14px; }
    .brand-logo-wrap {
      background: #ffffff; padding: 6px 12px; border-radius: 12px; display: flex; align-items: center; justify-content: center; box-shadow: 0 2px 8px rgba(0,0,0,0.15);
    }
    .brand-logo-svg { width: 48px; height: 48px; display: block; }
    .brand-title h1 { font-size: 1.25rem; font-weight: 800; letter-spacing: -0.02em; }
    .brand-title p { font-size: 0.8rem; color: #bae6fd; font-weight: 600; }

    /* Timer Widget with Sound Indicator */
    .timer-widget {
      display: flex; align-items: center; gap: 8px; background: rgba(255, 255, 255, 0.18);
      border: 1px solid rgba(255, 255, 255, 0.3); padding: 5px 14px; border-radius: 20px;
    }
    .timer-display {
      font-family: 'Segoe UI', monospace; font-size: 1.05rem; font-weight: 800; color: #ffffff; letter-spacing: 1px; min-width: 54px; text-align: center;
    }
    .timer-btn {
      background: #ffffff; border: none; color: var(--primary-dark); font-size: 0.75rem; font-weight: 700;
      padding: 4px 9px; border-radius: 12px; cursor: pointer; transition: all 0.2s;
    }
    .timer-btn:hover { background: #e0f2fe; color: var(--primary-blue); }

    /* Toast Notification for Timed Sound Reminders */
    .toast-reminder {
      display: none; position: fixed; bottom: 25px; right: 25px; background: #0c4a6e; color: #ffffff;
      padding: 14px 22px; border-radius: 14px; box-shadow: 0 10px 25px rgba(0,0,0,0.25); border: 2px solid var(--blue-border);
      z-index: 1000; font-weight: 700; font-size: 0.95rem; animation: slideUp 0.3s ease-out;
    }
    @keyframes slideUp { from { transform: translateY(20px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }

    .nav-tabs { display: flex; align-items: center; gap: 8px; flex-wrap: wrap; }
    .tab-btn {
      background: rgba(255, 255, 255, 0.18); border: 1px solid rgba(255, 255, 255, 0.3);
      color: #ffffff; padding: 7px 15px; border-radius: 20px; cursor: pointer; font-size: 0.86rem; font-weight: 600; transition: all 0.2s;
    }
    .tab-btn:hover, .tab-btn.active {
      background: #ffffff; color: var(--primary-blue); box-shadow: 0 2px 8px rgba(0,0,0,0.12);
    }
    .user-actions { display: flex; align-items: center; gap: 10px; flex-wrap: wrap; }
    .user-badge {
      background: rgba(255, 255, 255, 0.18); border: 1px solid rgba(255, 255, 255, 0.3);
      padding: 6px 14px; border-radius: 20px; font-size: 0.85rem; color: #f1f5f9; display: flex; align-items: center; gap: 6px;
    }
    .btn-icon {
      background: rgba(255, 255, 255, 0.22); border: none; color: #ffffff; padding: 8px 14px; border-radius: var(--radius-sm); cursor: pointer; font-size: 0.85rem; font-weight: 600; transition: all 0.2s;
    }
    .btn-icon:hover { background: rgba(255, 255, 255, 0.35); }

    main { max-width: 1440px; width: 100%; margin: 1.5rem auto; padding: 0 1rem; flex: 1; }
    .view-section { display: none; }
    .view-section.active { display: block; animation: fadeIn 0.25s ease-in-out; }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }

    /* Theory Notes Layout */
    .notes-card { max-width: 1100px; margin: 1rem auto 2rem auto; background: var(--card-white); border-radius: var(--radius-lg); padding: 2.5rem; border: 2px solid var(--blue-border-soft); box-shadow: var(--shadow-lg); }
    .notes-header { border-bottom: 2px solid var(--blue-border-soft); padding-bottom: 1.25rem; margin-bottom: 1.5rem; }
    .notes-header h2 { color: var(--primary-dark); font-size: 1.7rem; }
    .notes-body h3 { color: var(--primary-blue); margin: 1.8rem 0 0.6rem 0; font-size: 1.22rem; border-bottom: 1.5px solid var(--blue-border-soft); padding-bottom: 5px; display: flex; align-items: center; gap: 8px; }
    .notes-body p, .notes-body ul, .notes-body ol { color: var(--text-main); font-size: 1.02rem; line-height: 1.8; margin-bottom: 1rem; }
    .notes-body ul, .notes-body ol { padding-left: 1.6rem; }
    .formula-callout { background: #f0f9ff; border: 1px solid var(--blue-border-soft); border-left: 4px solid var(--primary-blue); padding: 14px 18px; border-radius: var(--radius-sm); margin: 14px 0; font-size: 1.05rem; }
    .step-badge { display: inline-block; background: #e0f2fe; color: #0369a1; font-weight: 800; font-size: 0.8rem; padding: 2px 10px; border-radius: 12px; margin-right: 6px; }

    /* Problem Grid Workspace */
    .learning-grid-layout { display: grid; grid-template-columns: 1fr 390px; gap: 1.5rem; align-items: start; }
    @media (max-width: 1080px) { .learning-grid-layout { grid-template-columns: 1fr; } }
    
    .problem-card { background: var(--card-white); border-radius: var(--radius-lg); padding: 2rem; box-shadow: var(--shadow-md); border: 2px solid var(--blue-border-soft); }
    .problem-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.25rem; padding-bottom: 0.75rem; border-bottom: 1.5px solid var(--blue-border-soft); }
    .p-tag { font-size: 1.15rem; font-weight: 800; color: var(--primary-blue); }
    .category-badge { background: #e0f2fe; color: var(--primary-dark); font-weight: 700; font-size: 0.8rem; padding: 3px 10px; border-radius: 6px; border: 1px solid var(--blue-border); margin-left: 8px; }
    .parts-badge { background: #fef3c7; color: #b45309; font-weight: 700; font-size: 0.8rem; padding: 3px 9px; border-radius: 6px; border: 1px solid #fde68a; margin-left: 6px; }
    .status-badge { font-size: 0.8rem; font-weight: 700; padding: 4px 10px; border-radius: 12px; text-transform: uppercase; }
    .badge-unvisited { background: #f8fafc; color: var(--text-muted); border: 1px solid #cbd5e1; }
    .badge-progress { background: #dbeafe; color: #1e40af; }
    .badge-complete { background: var(--correct-green-light); color: var(--correct-green); }
    .badge-skipped { background: #fef3c7; color: #b45309; }

    .problem-context { font-size: 1.15rem; font-weight: 500; margin-bottom: 1.25rem; background: #f0f9ff; border-left: 4px solid var(--accent-blue); padding: 16px 20px; border-radius: var(--radius-sm); line-height: 2.2; border: 1px solid var(--blue-border-soft); border-left-width: 4px; }

    /* Step Cards */
    .steps-container { display: flex; flex-direction: column; gap: 1.25rem; }
    .step-card { border: 2px solid var(--blue-border-soft); border-radius: var(--radius-md); padding: 1.25rem 1.5rem; background: #ffffff; transition: all 0.25s ease-in-out; }
    .step-card.active { border-color: var(--accent-blue); box-shadow: 0 4px 12px rgba(2, 132, 199, 0.15); }
    .step-card.completed { border-color: var(--correct-green); background: #fcfdfc; }
    
    .step-header-bar { display: flex; justify-content: space-between; align-items: center; margin-bottom: 0.75rem; }
    .step-title-text { font-weight: 700; font-size: 1rem; color: var(--primary-dark); }
    .step-status-indicator { font-size: 0.8rem; font-weight: 700; padding: 2px 8px; border-radius: 6px; }
    .step-card.completed .step-status-indicator { background: var(--correct-green-light); color: var(--correct-green); }
    .step-card.active .step-status-indicator { background: #e0f2fe; color: var(--primary-dark); }

    .step-prompt { font-size: 1.05rem; font-weight: 500; margin-bottom: 1rem; color: var(--text-main); line-height: 2.4; }

    /* Step Inputs */
    .step-input {
      display: inline-block; width: 180px; padding: 7px 11px; font-size: 1.05rem; font-weight: 700; font-family: 'Segoe UI', monospace;
      text-align: center; color: var(--primary-blue); background: #ffffff; border: 2px solid #7dd3fc; border-radius: var(--radius-sm); outline: none; margin: 0 4px; vertical-align: middle;
    }
    .step-input:focus { border-color: var(--primary-blue); box-shadow: 0 0 0 3px rgba(2, 132, 199, 0.2); }
    .step-input.input-correct { border-color: var(--correct-green) !important; background: var(--correct-green-light) !important; color: #065f46 !important; }
    .step-input.input-incorrect { border-color: var(--incorrect-red) !important; background: var(--incorrect-red-light) !important; color: #991b1b !important; }

    .step-controls { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; margin-top: 0.75rem; padding-top: 0.75rem; border-top: 1px dashed var(--blue-border-soft); }
    .step-feedback-msg { font-size: 0.88rem; font-weight: 600; }
    .step-feedback-msg.correct { color: #166534; }
    .step-feedback-msg.incorrect { color: #b91c1c; }

    /* Tools Panel */
    .tools-panel {
      background: #f0f9ff; border: 1.5px solid var(--blue-border); border-radius: var(--radius-md); padding: 1rem; margin-bottom: 1.25rem;
    }
    .tool-tab-header {
      display: flex; gap: 8px; border-bottom: 1.5px solid var(--blue-border-soft); padding-bottom: 8px; margin-bottom: 12px;
    }
    .tool-tab-btn {
      background: none; border: none; font-size: 0.85rem; font-weight: 700; color: var(--text-muted); cursor: pointer; padding: 4px 8px; border-radius: 4px;
    }
    .tool-tab-btn.active { color: var(--primary-blue); background: #e0f2fe; }
    .math-pad-grid { display: grid; grid-template-columns: repeat(7, 1fr); gap: 6px; }
    .math-pad-btn {
      background: #ffffff; border: 1px solid var(--blue-border); padding: 8px 4px; border-radius: var(--radius-sm); font-weight: 700; font-size: 0.95rem; cursor: pointer; text-align: center; color: var(--primary-dark);
    }
    .math-pad-btn:hover { background: var(--primary-blue); color: #ffffff; }

    /* Calculator View */
    .calc-box { background: #ffffff; border: 1.5px solid var(--blue-border); border-radius: var(--radius-sm); padding: 10px; }
    .calc-screen { width: 100%; background: #0c4a6e; color: #7dd3fc; font-family: monospace; font-size: 1.1rem; padding: 10px; border-radius: 4px; text-align: right; margin-bottom: 8px; overflow-x: auto; }
    .calc-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 6px; }
    .calc-btn { background: #f0f9ff; border: 1px solid var(--blue-border-soft); padding: 8px; border-radius: 4px; font-weight: 700; font-size: 0.9rem; cursor: pointer; text-align: center; color: var(--primary-dark); }
    .calc-btn:hover { background: #e0f2fe; }
    .calc-btn.op { background: #bae6fd; color: #0c4a6e; }
    .calc-btn.eq { background: var(--primary-blue); color: #fff; }

    /* Palette Sidebar */
    .palette-card { background: var(--card-white); border-radius: var(--radius-lg); padding: 1.25rem; border: 2px solid var(--blue-border-soft); position: sticky; top: 90px; box-shadow: var(--shadow-md); }
    .palette-grid { display: grid; grid-template-columns: repeat(5, 1fr); gap: 6px; margin: 1rem 0; max-height: 380px; overflow-y: auto; padding-right: 4px; }
    .palette-btn { aspect-ratio: 1; border-radius: var(--radius-sm); border: 1.5px solid var(--blue-border-soft); background: #f8fafc; color: var(--text-muted); font-weight: 700; cursor: pointer; display: flex; align-items: center; justify-content: center; font-size: 0.85rem; }
    .palette-btn.active { border: 2.5px solid var(--primary-blue) !important; background: #e0f2fe !important; color: var(--primary-blue) !important; }
    .palette-btn.completed { background: var(--correct-green) !important; color: #ffffff !important; border-color: var(--correct-green) !important; }
    .palette-btn.progress { background: #93c5fd !important; border-color: #3b82f6 !important; color: #0f172a !important; }
    .palette-btn.skipped { background: #fef3c7 !important; color: #b45309 !important; border-color: #fde68a !important; }

    .problem-action-bar { display: flex; justify-content: space-between; align-items: center; padding-top: 1.25rem; border-top: 1.5px solid var(--blue-border-soft); margin-top: 1.5rem; flex-wrap: wrap; gap: 10px; }
    .btn { padding: 9px 16px; border-radius: var(--radius-sm); font-weight: 700; font-size: 0.92rem; cursor: pointer; border: none; display: inline-flex; align-items: center; gap: 6px; transition: all 0.2s ease; }
    .btn-step-check { background: var(--primary-blue); color: #ffffff; }
    .btn-step-back { background: #f0f9ff; color: var(--primary-dark); border: 1px solid var(--blue-border); }
    .btn-secondary { background: #e2e8f0; color: var(--text-main); }
    .btn-skip { background: #ffffff; color: var(--brand-gold-dark); border: 1.5px solid var(--brand-gold-dark); }

    /* Score Report */
    .score-hero-card { background: linear-gradient(135deg, var(--primary-dark) 0%, var(--primary-blue) 60%, var(--accent-blue) 100%); color: #ffffff; border-radius: var(--radius-lg); padding: 2.5rem 2rem; text-align: center; margin-bottom: 2rem; box-shadow: var(--shadow-lg); }
    .score-circle { width: 115px; height: 115px; border-radius: 50%; background: rgba(255,255,255,0.15); border: 4px solid #7dd3fc; display: flex; flex-direction: column; align-items: center; justify-content: center; margin: 0 auto 1rem auto; }
    .stats-row { display: grid; grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); gap: 1rem; max-width: 600px; margin: 1.5rem auto 0 auto; }
    .stat-pill { background: rgba(255,255,255,0.12); padding: 10px; border-radius: var(--radius-md); }
    .review-card { background: #ffffff; border: 2px solid var(--blue-border-soft); border-radius: var(--radius-md); padding: 1.5rem; margin-bottom: 1rem; box-shadow: var(--shadow-sm); line-height: 2.2; }
  </style>
</head>
<body>

  <!-- Header -->
  <header>
    <div class="header-container">
      <div class="brand-group">
        <div class="brand-logo-wrap">
          <svg class="brand-logo-svg" viewBox="0 0 160 160" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M45 42 C66 22, 94 22, 115 42" stroke="#f59e0b" stroke-width="8" stroke-linecap="round" fill="none"/>
            <path d="M56 56 C70 42, 90 42, 104 56" stroke="#f59e0b" stroke-width="8" stroke-linecap="round" fill="none"/>
            <path d="M68 70 C75 62, 85 62, 92 70" stroke="#f59e0b" stroke-width="7" stroke-linecap="round" fill="none"/>
            <path d="M25 80 L76 96 L76 136 L25 120 Z" stroke="#334155" stroke-width="7" fill="#ffffff" stroke-linejoin="round"/>
            <path d="M135 80 L84 96 L84 136 L135 120 Z" stroke="#334155" stroke-width="7" fill="#ffffff" stroke-linejoin="round"/>
            <line x1="40" y1="94" x2="68" y2="103" stroke="#334155" stroke-width="5" stroke-linecap="round"/>
            <line x1="40" y1="108" x2="68" y2="117" stroke="#334155" stroke-width="5" stroke-linecap="round"/>
            <line x1="120" y1="94" x2="92" y2="103" stroke="#334155" stroke-width="5" stroke-linecap="round"/>
            <line x1="120" y1="108" x2="92" y2="117" stroke="#334155" stroke-width="5" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="brand-title">
          <h1>Brain &amp; Mind Academy</h1>
          <p>B&amp;M - The Experts • Solving Equations with Variables on Both Sides</p>
        </div>
      </div>

      <!-- Live Interactive Stopwatch / Timer with Sound Alerts -->
      <div class="timer-widget">
        <span style="font-size:0.9rem;">⏱️</span>
        <span class="timer-display" id="timerDisplay">00:00</span>
        <button class="timer-btn" id="timerToggleBtn" onclick="toggleTimer()">Pause</button>
        <button class="timer-btn" onclick="resetTimer()">Reset</button>
        <button class="timer-btn" style="background:#e0f2fe; color:var(--primary-dark);" onclick="playReminderChime()">🔔 Test Sound</button>
      </div>

      <div class="nav-tabs">
        <button class="tab-btn active" onclick="switchMainTab('theory')">📖 Theory &amp; Modeling Guide</button>
        <button class="tab-btn" onclick="switchMainTab('sheet')">✍️ Practice Sheet (Questions 1–15)</button>
        <button class="tab-btn" onclick="switchMainTab('solutions')">📋 Complete Solutions</button>
      </div>
      <div class="user-actions">
        <div class="user-badge"><span id="userEmailSpan">Student</span></div>
        <button class="btn-icon" id="soundToggleBtn"><span id="soundIcon">🔊</span></button>
      </div>
    </div>
  </header>

  <!-- Notification Banner for 20-min and 5-min Audio Reminders -->
  <div id="reminderToast" class="toast-reminder"></div>

  <main>
    
    <!-- 1. Theory Notes Tab -->
    <section id="theoryView" class="view-section active">
      <div class="notes-card">
        <div class="notes-header">
          <h2>Solving Equations with Variables on Both Sides: Complete Method Guide</h2>
          <p style="color: var(--text-muted); font-size: 0.95rem;">Step-by-step mathematical procedures to simplify expressions, collect variable terms, clear fractions and decimals, and analyze special solutions.</p>
        </div>

        <div class="notes-body">
          <h3><span class="step-badge">STEP 1</span> Simplify Each Side Independently</h3>
          <p>Before applying inverse operations across the equals sign, clear parentheses using the <strong>Distributive Property</strong> and combine like terms on each side of the equation separately:</p>
          <div class="formula-callout">
            <strong>Example Demonstration:</strong> Solve \( 3x - 10 + 4x = -2(x - 4) + 9 \)<br>
            • Left Side: Combine like terms \( 3x + 4x = 7x \implies 7x - 10 \)<br>
            • Right Side: Distribute \( -2 \): \( -2x + 8 + 9 = -2x + 17 \)<br>
            • Simplified Equation: \( 7x - 10 = -2x + 17 \)
          </div>

          <h3><span class="step-badge">STEP 2</span> Collect Variable Terms on One Side</h3>
          <p>Use addition or subtraction to move all variable terms to one side of the equation and all constant numbers to the other:</p>
          <div class="formula-callout">
            • Add \( 2x \) to both sides: \( 7x + 2x - 10 = 17 \implies 9x - 10 = 17 \)<br>
            • Add \( 10 \) to both sides: \( 9x = 27 \)<br>
            • Divide by \( 9 \): \( x = 3 \)
          </div>

          <h3><span class="step-badge">STEP 3</span> Clearing Fractions &amp; Decimals</h3>
          <p>Eliminate fractions by multiplying every term on both sides by the <strong>Least Common Denominator (LCD)</strong>, or clear decimals by multiplying by powers of 10 (\(10, 100, 1000\)):</p>
          <div class="formula-callout">
            <strong>Fraction Example:</strong> \( \frac{1}{2}(n - 4) - 7 = -2n + 6 \)<br>
            • Add 7 to isolate the fraction term: \( \frac{1}{2}(n - 4) = -2n + 13 \)<br>
            • Multiply each side by 2: \( n - 4 = -4n + 26 \)<br>
            • Collect variable terms: \( 5n = 30 \implies n = 6 \)
          </div>

          <h3><span class="step-badge">STEP 4</span> Identifying Special Solutions: Identities vs. No Solution</h3>
          <p>When collecting variable terms causes the variable to cancel out completely from both sides, examine the resulting numerical statement:</p>
          <ul>
            <li><strong>Identity (Infinitely Many Solutions):</strong> Results in a true numerical statement such as \( -12 = -12 \) or \( 0 = 0 \). Any real number is a solution.</li>
            <li><strong>Contradiction (No Solution):</strong> Results in a false numerical statement such as \( -4 = -8 \) or \( 0 = 5 \). No real number satisfies the equation.</li>
          </ul>

          <h3><span class="step-badge">STEP 5</span> Real-World Break-Even &amp; Mixture Modeling</h3>
          <p>Set two cost or value expressions equal to determine the point of equality:</p>
          <div class="formula-callout">
            • <strong>Break-Even Cost Models:</strong> \( \text{Cost}_1(x) = \text{Cost}_2(x) \). Solving for \( x \) yields the break-even quantity where both options cost the exact same amount.<br>
            • <strong>Mixture Equations:</strong> \( \text{Cost}_A \cdot a + \text{Cost}_B \cdot b = \text{Cost}_{\text{blend}} \cdot (a + b) \).
          </div>
        </div>

        <div style="margin-top:2rem; background:#f0f9ff; border:2px solid var(--blue-border); border-radius:var(--radius-md); padding:1.5rem; display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:1rem;">
          <div>
            <strong>Ready to practice the 15 questions sequentially?</strong>
            <p style="font-size: 0.9rem; color: var(--primary-dark); margin-top:2px;">Complete each algebraic step and applied modeling task with instant auto-verification.</p>
          </div>
          <button class="btn btn-primary" onclick="switchMainTab('sheet')" style="background:var(--primary-blue); color:#fff;">
            Start 15-Question Practice Sheet →
          </button>
        </div>
      </div>
    </section>

    <!-- 2. Guided Practice Sheet (Interactive Workspace) -->
    <section id="sheetView" class="view-section">
      <div class="learning-grid-layout">
        
        <!-- Left Side: Active Problem & Step Sequence -->
        <div class="problem-card">
          <div class="problem-header">
            <div>
              <span class="p-tag" id="pNumberDisplay">Question 1</span>
              <span class="category-badge" id="pCategoryBadge">Explore &amp; Reason</span>
              <span class="parts-badge" id="pPartsBadge">3 Steps</span>
            </div>
            <div class="status-badge badge-unvisited" id="pStatusBadge">Unvisited</div>
          </div>
          
          <div class="problem-context" id="pContextDisplay"></div>

          <!-- On-Screen Mathematical Keypad & Calculator -->
          <div class="tools-panel">
            <div class="tool-tab-header">
              <button class="tool-tab-btn active" id="tabPadBtn" onclick="switchToolTab('pad')">⌨️ Mathematical Keypad</button>
              <button class="tool-tab-btn" id="tabCalcBtn" onclick="switchToolTab('calc')">🧮 Calculator</button>
            </div>
            
            <div id="mathPadView">
              <div class="math-pad-grid">
                <button class="math-pad-btn" onclick="insertSymbol('x')">x</button>
                <button class="math-pad-btn" onclick="insertSymbol('n')">n</button>
                <button class="math-pad-btn" onclick="insertSymbol('z')">z</button>
                <button class="math-pad-btn" onclick="insertSymbol('d')">d</button>
                <button class="math-pad-btn" onclick="insertSymbol('a')">a</button>
                <button class="math-pad-btn" onclick="insertSymbol('s')">s</button>
                <button class="math-pad-btn" onclick="insertSymbol('h')">h</button>
                <button class="math-pad-btn" onclick="insertSymbol('y')">y</button>
                <button class="math-pad-btn" onclick="insertSymbol('g')">g</button>
                <button class="math-pad-btn" onclick="insertSymbol('.')">.</button>
                <button class="math-pad-btn" onclick="insertSymbol('/')">/</button>
                <button class="math-pad-btn" onclick="insertSymbol('-')">-</button>
                <button class="math-pad-btn" onclick="insertSymbol('+')">+</button>
                <button class="math-pad-btn" onclick="insertSymbol('(')">(</button>
                <button class="math-pad-btn" onclick="insertSymbol(')')">)</button>
                <button class="math-pad-btn" onclick="insertSymbol('None')">None</button>
                <button class="math-pad-btn" onclick="insertSymbol('No solution')">No solution</button>
                <button class="math-pad-btn" onclick="insertSymbol('Identity')">Identity</button>
                <button class="math-pad-btn" style="background:#fee2e2; color:#dc2626;" onclick="clearActiveField()">Clear</button>
              </div>
            </div>

            <div id="calcView" style="display:none;">
              <div class="calc-box">
                <div class="calc-screen" id="calcScreen">0</div>
                <div class="calc-grid">
                  <button class="calc-btn" onclick="calcAppend('(')">(</button>
                  <button class="calc-btn" onclick="calcAppend(')')">)</button>
                  <button class="calc-btn" onclick="calcClear()">C</button>
                  <button class="calc-btn op" onclick="calcAppend('/')">/</button>
                  <button class="calc-btn" onclick="calcAppend('7')">7</button>
                  <button class="calc-btn" onclick="calcAppend('8')">8</button>
                  <button class="calc-btn" onclick="calcAppend('9')">9</button>
                  <button class="calc-btn op" onclick="calcAppend('*')">*</button>
                  <button class="calc-btn" onclick="calcAppend('4')">4</button>
                  <button class="calc-btn" onclick="calcAppend('5')">5</button>
                  <button class="calc-btn" onclick="calcAppend('6')">6</button>
                  <button class="calc-btn op" onclick="calcAppend('-')">-</button>
                  <button class="calc-btn" onclick="calcAppend('1')">1</button>
                  <button class="calc-btn" onclick="calcAppend('2')">2</button>
                  <button class="calc-btn" onclick="calcAppend('3')">3</button>
                  <button class="calc-btn op" onclick="calcAppend('+')">+</button>
                  <button class="calc-btn" onclick="calcAppend('0')">0</button>
                  <button class="calc-btn" onclick="calcAppend('.')">.</button>
                  <button class="calc-btn op" onclick="calcSqrt()">√</button>
                  <button class="calc-btn eq" onclick="calcEval()">=</button>
                </div>
              </div>
            </div>
          </div>

          <!-- Progressive Step Stack -->
          <div class="steps-container" id="stepsListContainer"></div>

          <!-- Problem Navigation Bar -->
          <div class="problem-action-bar">
            <div style="display: flex; gap: 8px;">
              <button class="btn btn-secondary" id="prevProblemBtn">← Prev Question</button>
              <button class="btn btn-secondary" id="nextProblemBtn">Next Question →</button>
            </div>
            <button class="btn btn-skip" id="skipProblemBtn">Skip Question</button>
          </div>
        </div>

        <!-- Right Side: Sidebar Navigation Palette -->
        <aside class="palette-card">
          <div style="display:flex; justify-content:space-between; align-items:center;">
            <strong style="color:var(--primary-dark); font-size:1.02rem;">15-Question Index</strong>
            <span style="font-size:0.85rem; color:var(--primary-blue); font-weight:700;" id="completionRateText">0/15 Solved</span>
          </div>
          <div class="palette-grid" id="paletteGridContainer"></div>
          <button class="btn btn-primary" id="finishAssessmentBtn" style="margin-top: 1.25rem; width: 100%; background:var(--primary-blue); color:#fff;">Finish &amp; View All Solutions</button>
        </aside>

      </div>
    </section>

    <!-- 3. Final Review & Complete Solutions -->
    <section id="solutionsView" class="view-section">
      <div class="score-hero-card">
        <span style="background:rgba(255,255,255,0.2); color:#bae6fd; padding:4px 10px; border-radius:12px; font-weight:700;">Performance Report</span>
        <h2 style="margin: 0.5rem 0; font-size: 1.7rem;">Variables on Both Sides Mastery Report</h2>
        <div class="score-circle">
          <div id="finalScoreVal" style="font-size:2rem; font-weight:800;">0</div>
          <div style="font-size:0.8rem; color:#bae6fd;">out of 15</div>
        </div>
        <p id="performanceFeedbackDesc" style="color: #bae6fd; font-size:0.95rem; max-width:540px; margin:0 auto;"></p>
        <div class="stats-row">
          <div class="stat-pill"><div style="font-size:0.75rem; color:#bae6fd;">Accuracy</div><div id="accuracyStat" style="font-size:1.2rem; font-weight:700;">0%</div></div>
          <div class="stat-pill"><div style="font-size:0.75rem; color:#bae6fd;">Solved</div><div id="correctCountStat" style="font-size:1.2rem; font-weight:700; color:#86efac;">0</div></div>
          <div class="stat-pill"><div style="font-size:0.75rem; color:#bae6fd;">Skipped</div><div id="skippedCountStat" style="font-size:1.2rem; font-weight:700; color:#fde047;">0</div></div>
        </div>
        <div style="margin-top: 1.5rem; display:flex; justify-content:center; gap:10px;">
          <button class="btn" style="background: rgba(255,255,255,0.25); color:#fff;" id="retakeQuizBtn">↺ Retake Learning Sheet</button>
          <button class="btn" style="background:#fff; color:var(--primary-dark);" onclick="window.print()">🖨️ Print Solutions</button>
        </div>
      </div>
      <h3 style="color: var(--primary-dark); margin-bottom:1rem;">Complete Step-by-Step Mathematical Solutions (Questions 1 to 15)</h3>
      <div id="reviewListContainer"></div>
    </section>

  </main>

  <script>
    /* ==========================================================================
       COMPLETE 15-QUESTION DATASET (RENUMBERED SEQUENTIALLY FROM 1)
       ========================================================================== */
    const PROBLEMS_DATA = [
      // Q1: Explore & Reason (image_e319c9.jpg)
      {
        id: 1,
        title: "Question 1",
        category: "Explore & Reason",
        partsInfo: "3 Steps Required",
        context: "Friends want to see a movie at two theaters and share 3 tubs of popcorn.<br>• Theater A: Ticket $14.50, Popcorn $5.75 per tub<br>• Theater B: Ticket $13.00, Popcorn $6.75 per tub",
        steps: [
          {
            title: "Step 1: Total Popcorn Cost at Each Theater",
            prompt: "Popcorn cost at Theater A is \\( 3 \\times \\$5.75 = \\$17.25 \\). Popcorn cost at Theater B is \\( 3 \\times \\$6.75 = \\$ \\) <input class='step-input' style='width:70px;' data-ans='20.25'>",
            explanation: "\\( 3 \\times 6.75 = \\$20.25 \\)."
          },
          {
            title: "Step 2: Set Up the Break-Even Cost Equation",
            prompt: "Let \\( x \\) be the number of friends. Total cost equation: \\( 14.50x + 17.25 = 13.00x + 20.25 \\). Subtract \\( 13x \\) and \\( 17.25 \\): \\( 1.5x = \\) <input class='step-input' style='width:50px;' data-ans='3'>",
            explanation: "\\( 14.50x - 13.00x = 20.25 - 17.25 \\implies 1.5x = 3 \\)."
          },
          {
            title: "Step 3: Number of Friends for Identical Total Cost",
            prompt: "Divide by 1.5: \\( x = \\frac{3}{1.5} = \\) <input class='step-input' style='width:50px;' data-ans='2'> friends",
            explanation: "\\( x = 2 \\) friends. For fewer than 2 friends Theater A is cheaper, and for more than 2 friends Theater B is cheaper."
          }
        ]
      },
      // Q2: Example 1A (image_e31c8e.jpg)
      {
        id: 2,
        title: "Question 2",
        category: "Multi-Step Linear",
        partsInfo: "3 Steps Required",
        context: "Find the value of \\( x \\) in the equation: \\[ 3x - 10 + 4x = -2(x - 4) + 9 \\]",
        steps: [
          {
            title: "Step 1: Simplify Both Sides Independently",
            prompt: "Left side: \\( 3x + 4x - 10 = 7x - 10 \\). Right side: \\( -2x + 8 + 9 = -2x + k \\). What is \\( k \\)? <input class='step-input' style='width:50px;' data-ans='17'>",
            explanation: "\\( -2(x - 4) + 9 = -2x + 8 + 9 = -2x + 17 \\)."
          },
          {
            title: "Step 2: Collect Variable and Constant Terms",
            prompt: "Add \\( 2x \\) and add 10 to both sides: \\( 7x + 2x = 17 + 10 \\implies 9x = \\) <input class='step-input' style='width:50px;' data-ans='27'>",
            explanation: "\\( 9x = 27 \\)."
          },
          {
            title: "Step 3: Solve for x",
            prompt: "Divide by 9: \\( x = \\frac{27}{9} = \\) <input class='step-input' style='width:50px;' data-ans='3'>",
            explanation: "\\( x = 3 \\)."
          }
        ]
      },
      // Q3: Example 1B (image_e31c8e.jpg)
      {
        id: 3,
        title: "Question 3",
        category: "Fraction Elimination",
        partsInfo: "3 Steps Required",
        context: "Find the value of \\( n \\) in the equation: \\[ \\frac{1}{2}(n - 4) - 7 = -2n + 6 \\]",
        steps: [
          {
            title: "Step 1: Isolate the Fraction Term",
            prompt: "Add 7 to both sides: \\( \\frac{1}{2}(n - 4) = -2n + 6 + 7 = -2n + \\) <input class='step-input' style='width:50px;' data-ans='13'>",
            explanation: "\\( \\frac{1}{2}(n - 4) = -2n + 13 \\)."
          },
          {
            title: "Step 2: Multiply Each Side by 2 to Clear the Fraction",
            prompt: "\\( n - 4 = 2(-2n + 13) = -4n + \\) <input class='step-input' style='width:50px;' data-ans='26'>",
            explanation: "\\( n - 4 = -4n + 26 \\)."
          },
          {
            title: "Step 3: Collect Like Terms and Solve for n",
            prompt: "\\( n + 4n = 26 + 4 \\implies 5n = 30 \\implies n = \\) <input class='step-input' style='width:50px;' data-ans='6'>",
            explanation: "\\( n = \\frac{30}{5} = 6 \\)."
          }
        ]
      },
      // Q4: Problem 1a (image_e31cca.png)
      {
        id: 4,
        title: "Question 4",
        category: "Distributive & Decimals",
        partsInfo: "3 Steps Required",
        context: "Solve the equation: \\[ 100(z - 0.2) = -10(5z + 0.8) \\]",
        steps: [
          {
            title: "Step 1: Divide Both Sides by 10 or Expand",
            prompt: "Dividing by 10 gives \\( 10(z - 0.2) = -(5z + 0.8) \\implies 10z - 2 = -5z - \\) <input class='step-input' style='width:60px;' data-ans='0.8'>",
            explanation: "\\( 10z - 2 = -5z - 0.8 \\)."
          },
          {
            title: "Step 2: Collect Variable and Constant Terms",
            prompt: "Add \\( 5z \\) and add 2 to both sides: \\( 15z = -0.8 + 2 = \\) <input class='step-input' style='width:60px;' data-ans='1.2'>",
            explanation: "\\( 15z = 1.2 \\)."
          },
          {
            title: "Step 3: Solve for z",
            prompt: "Divide by 15: \\( z = \\frac{1.2}{15} = \\) <input class='step-input' style='width:70px;' data-ans='0.08' data-alt='2/25'>",
            explanation: "\\( z = 0.08 \\) (or \\( \\frac{2}{25} \\))."
          }
        ]
      },
      // Q5: Problem 1b (image_e31cca.png)
      {
        id: 5,
        title: "Question 5",
        category: "Fraction & Distribution",
        partsInfo: "3 Steps Required",
        context: "Solve the equation: \\[ \\frac{5}{8}(16d + 24) = 6(d - 1) + 1 \\]",
        steps: [
          {
            title: "Step 1: Expand the Left Side",
            prompt: "\\( \\frac{5}{8}(16d) + \\frac{5}{8}(24) = 10d + \\) <input class='step-input' style='width:50px;' data-ans='15'>",
            explanation: "\\( 10d + 15 \\)."
          },
          {
            title: "Step 2: Expand and Simplify the Right Side",
            prompt: "\\( 6(d - 1) + 1 = 6d - 6 + 1 = 6d - \\) <input class='step-input' style='width:50px;' data-ans='5'>",
            explanation: "\\( 6d - 5 \\)."
          },
          {
            title: "Step 3: Solve for d",
            prompt: "\\( 10d - 6d = -5 - 15 \\implies 4d = -20 \\implies d = \\) <input class='step-input' style='width:60px;' data-ans='-5'>",
            explanation: "\\( d = \\frac{-20}{4} = -5 \\)."
          }
        ]
      },
      // Q6: Coffee Mixture Problem (image_e31ced.jpg)
      {
        id: 6,
        title: "Question 6",
        category: "Mixture Modeling",
        partsInfo: "3 Steps Required",
        context: "Arabica coffee costs $28/lb and Robusta coffee costs $8.75/lb. How many pounds \\( a \\) of Arabica coffee must be mixed with 3 pounds of Robusta to create a blend costing $15.50/lb?",
        steps: [
          {
            title: "Step 1: Write the Mixture Equation",
            prompt: "Total cost of Arabica ($28a) + Robusta (\\( 3 \\times 8.75 = 26.25 \\)) equals \\( 15.50(a + 3) \\). Expand the right side: \\( 15.5a + \\) <input class='step-input' style='width:60px;' data-ans='46.5'>",
            explanation: "\\( 15.5(a + 3) = 15.5a + 46.5 \\)."
          },
          {
            title: "Step 2: Collect Like Terms",
            prompt: "\\( 28a - 15.5a = 46.5 - 26.25 \\implies 12.5a = \\) <input class='step-input' style='width:70px;' data-ans='20.25'>",
            explanation: "\\( 12.5a = 20.25 \\)."
          },
          {
            title: "Step 3: Solve for Pounds of Arabica Coffee",
            prompt: "\\( a = \\frac{20.25}{12.5} = \\) <input class='step-input' style='width:70px;' data-ans='1.62'> pounds",
            explanation: "You must mix 1.62 pounds of Arabica coffee."
          }
        ]
      },
      // Q7: Example 4 (image_e31d28.jpg)
      {
        id: 7,
        title: "Question 7",
        category: "Cost Modeling",
        partsInfo: "2 Steps Required",
        context: "Cameron pays $0.95 per song currently. A new service charges $0.89 per song with a $12 joining fee. At how many songs \\( s \\) is the cost identical?",
        steps: [
          {
            title: "Step 1: Set Up and Isolate Variable Terms",
            prompt: "\\( 0.89s + 12 = 0.95s \\implies 12 = 0.95s - 0.89s = \\) <input class='step-input' style='width:70px;' data-ans='0.06'> \\( s \\)",
            explanation: "\\( 12 = 0.06s \\)."
          },
          {
            title: "Step 2: Solve for Number of Songs",
            prompt: "\\( s = \\frac{12}{0.06} = \\) <input class='step-input' style='width:60px;' data-ans='200'> songs",
            explanation: "Both services cost the same at 200 songs. If he downloads more than 200 songs, he should switch."
          }
        ]
      },
      // Q8: Problem 4 (image_e31d49.png)
      {
        id: 8,
        title: "Question 8",
        category: "Comparative Modeling",
        partsInfo: "2 Steps Required",
        context: "A third music service charges a $15 joining fee and $0.80 per song. At what number of songs does it become less expensive than Cameron's current service ($0.95/song)?",
        steps: [
          {
            title: "Step 1: Find the Break-Even Quantity",
            prompt: "\\( 0.80s + 15 = 0.95s \\implies 15 = 0.15s \\implies s = \\frac{15}{0.15} = \\) <input class='step-input' style='width:60px;' data-ans='100'> songs",
            explanation: "\\( 15 = 0.15s \\implies s = 100 \\)."
          },
          {
            title: "Step 2: State Condition for Less Expensive Option",
            prompt: "Since the per-song rate is lower, the new service is less expensive when the number of songs is strictly greater than: <input class='step-input' style='width:60px;' data-ans='100'>",
            explanation: "For more than 100 songs (\\( s > 100 \\)), the third service costs less."
          }
        ]
      },
      // Q9: Problem 5 (image_e3204c.jpg)
      {
        id: 9,
        title: "Question 9",
        category: "Linear Equation",
        partsInfo: "2 Steps Required",
        context: "Solve the linear equation: \\[ 5(2x + 6) = 8x + 48 \\]",
        steps: [
          {
            title: "Step 1: Distribute and Collect Variables",
            prompt: "\\( 10x + 30 = 8x + 48 \\implies 10x - 8x = 48 - 30 \\implies 2x = \\) <input class='step-input' style='width:50px;' data-ans='18'>",
            explanation: "\\( 2x = 18 \\)."
          },
          {
            title: "Step 2: Solve for x",
            prompt: "Divide by 2: \\( x = \\) <input class='step-input' style='width:50px;' data-ans='9'>",
            explanation: "\\( x = 9 \\)."
          }
        ]
      },
      // Q10: Problem 6 (image_e3204c.jpg)
      {
        id: 10,
        title: "Question 10",
        category: "Linear Equation",
        partsInfo: "2 Steps Required",
        context: "Solve the linear equation: \\[ -3(8 + 3h) = 5h + 4 \\]",
        steps: [
          {
            title: "Step 1: Distribute and Collect Variable Terms",
            prompt: "\\( -24 - 9h = 5h + 4 \\implies -9h - 5h = 4 + 24 \\implies -14h = \\) <input class='step-input' style='width:50px;' data-ans='28'>",
            explanation: "\\( -14h = 28 \\)."
          },
          {
            title: "Step 2: Solve for h",
            prompt: "Divide by -14: \\( h = \\) <input class='step-input' style='width:50px;' data-ans='-2'>",
            explanation: "\\( h = \\frac{28}{-14} = -2 \\)."
          }
        ]
      },
      // Q11: Problem 7 (image_e3204c.jpg)
      {
        id: 11,
        title: "Question 11",
        category: "Special Case: Identity",
        partsInfo: "2 Steps Required",
        context: "Solve the linear equation: \\[ 2(y - 6) = 3(y - 4) - y \\]",
        steps: [
          {
            title: "Step 1: Expand and Simplify Both Sides",
            prompt: "Left side: \\( 2y - 12 \\). Right side: \\( 3y - 12 - y = \\) <input class='step-input' style='width:90px;' data-ans='2y-12' data-alt='2y - 12'>",
            explanation: "\\( 3y - y - 12 = 2y - 12 \\)."
          },
          {
            title: "Step 2: Classify the Solution",
            prompt: "Subtracting \\( 2y \\) yields \\( -12 = -12 \\), an identity true for all real numbers. Enter 'Identity' or 'Infinitely many solutions': <input class='step-input' style='width:160px;' data-ans='Identity' data-alt='infinitely many solutions|infinite solutions|all real numbers'>",
            explanation: "Because both sides are identical, there are infinitely many solutions (an identity)."
          }
        ]
      },
      // Q12: Problem 8 (image_e3204c.jpg)
      {
        id: 12,
        title: "Question 12",
        category: "Special Case: Contradiction",
        partsInfo: "2 Steps Required",
        context: "Solve the linear equation: \\[ 8x - 4 = 2(4x - 4) \\]",
        steps: [
          {
            title: "Step 1: Expand the Right Side",
            prompt: "\\( 8x - 4 = 8x - \\) <input class='step-input' style='width:50px;' data-ans='8'>",
            explanation: "\\( 2(4x - 4) = 8x - 8 \\)."
          },
          {
            title: "Step 2: Determine Number of Solutions",
            prompt: "Subtracting \\( 8x \\) gives \\( -4 = -8 \\), which is false. Enter 'No solution': <input class='step-input' style='width:120px;' data-ans='No solution' data-alt='no solution|none'>",
            explanation: "A false statement with no variables remaining indicates no solution."
          }
        ]
      },
      // Q13: Problem 9 (image_e3204c.jpg)
      {
        id: 13,
        title: "Question 13",
        category: "Bowling Break-Even",
        partsInfo: "2 Steps Required",
        context: "For how many games is the total cost of bowling equal for the two establishments?<br>• Family Bowling: $4.00 per game + $1.00 shoe rental<br>• Knight Owl Bowling: $3.75 per game + $2.00 shoe rental",
        steps: [
          {
            title: "Step 1: Set Up the Equation",
            prompt: "\\( 4.00g + 1.00 = 3.75g + 2.00 \\implies 4g - 3.75g = 2 - 1 \\implies 0.25g = \\) <input class='step-input' style='width:50px;' data-ans='1'>",
            explanation: "\\( 0.25g = 1 \\)."
          },
          {
            title: "Step 2: Solve for Number of Games",
            prompt: "\\( g = \\frac{1}{0.25} = \\) <input class='step-input' style='width:50px;' data-ans='4'> games",
            explanation: "\\( g = 4 \\) games."
          }
        ]
      },
      // Q14: Problem 14 (image_e320ac.jpg)
      {
        id: 14,
        title: "Question 14",
        category: "Geometry Connection",
        partsInfo: "3 Steps Required",
        context: "The triangle shown is isosceles with congruent leg lengths \\( (5n - 17) \\text{ cm} \\) and \\( (2n + 1) \\text{ cm} \\), and base \\( n \\text{ cm} \\).",
        steps: [
          {
            title: "Step 1: Solve for n",
            prompt: "\\( 5n - 17 = 2n + 1 \\implies 3n = 18 \\implies n = \\) <input class='step-input' style='width:50px;' data-ans='6'>",
            explanation: "\\( 5n - 2n = 1 + 17 \\implies 3n = 18 \\implies n = 6 \\)."
          },
          {
            title: "Step 2: Find the Length of Each Leg",
            prompt: "Leg length = \\( 2(6) + 1 = \\) <input class='step-input' style='width:50px;' data-ans='13'> cm",
            explanation: "\\( 2(6) + 1 = 13 \\) cm (and \\( 5(6) - 17 = 13 \\) cm)."
          },
          {
            title: "Step 3: Calculate the Perimeter of the Triangle",
            prompt: "Perimeter = \\( 13 + 13 + 6 = \\) <input class='step-input' style='width:60px;' data-ans='32'> cm",
            explanation: "Perimeter = \\( 13 + 13 + 6 = 32 \\) cm."
          }
        ]
      },
      // Q15: Problem 15 (image_e320ac.jpg)
      {
        id: 15,
        title: "Question 15",
        category: "Higher Order Thinking",
        partsInfo: "3 Steps Required",
        context: "The equation shown has a missing value in the box: \\[ -2(2x - \\Box) + 1 = 17 - 4x \\]",
        steps: [
          {
            title: "Step 1: Value for Identity (Infinitely Many Solutions)",
            prompt: "Expanding gives \\( -4x + 2\\Box + 1 = -4x + 17 \\implies 2\\Box + 1 = 17 \\implies 2\\Box = 16 \\). What is \\( \\Box \\)? <input class='step-input' style='width:50px;' data-ans='8'>",
            explanation: "\\( 2\\Box = 16 \\implies \\Box = 8 \\)."
          },
          {
            title: "Step 2: Value(s) for Exactly One Solution",
            prompt: "Because the coefficients of \\( x \\) are identical on both sides (\\( -4x \\) and \\( -4x \\)), the variable always cancels. Can any value of \\( \\Box \\) yield exactly one solution? Enter 'None': <input class='step-input' style='width:80px;' data-ans='None' data-alt='none|no value'>",
            explanation: "There is no value of the box that gives exactly one solution because the variable terms cancel regardless of the box."
          },
          {
            title: "Step 3: Condition for No Solution",
            prompt: "For the equation to be a contradiction (no solution), \\( 2\\Box + 1 \\neq 17 \\). Thus, what single number must \\( \\Box \\) NOT equal? Enter the number: <input class='step-input' style='width:50px;' data-ans='8'>",
            explanation: "Any real number except 8 produces no solution (\\( \\Box \\neq 8 \\))."
          }
        ]
      }
    ];

    /* ==========================================================================
       STOPWATCH / TIMER WITH 20-MIN & 5-MIN SOUND REMINDERS
       ========================================================================== */
    let timerSeconds = 0;
    let timerInterval = null;
    let timerRunning = false;

    function formatTime(totalSecs) {
      const mins = Math.floor(totalSecs / 60);
      const secs = totalSecs % 60;
      return `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
    }

    function checkTimerSoundMilestones(secs) {
      // Exactly at 20 minutes (1200 seconds)
      if (secs === 1200) {
        playReminderChime();
        showToast("⏰ Milestone: 20 minutes elapsed! Great effort, keep going!");
      } 
      // Every 5 minutes after 20 minutes (1500s, 1800s, 2100s, etc.)
      else if (secs > 1200 && (secs - 1200) % 300 === 0) {
        playReminderChime();
        const mins = Math.floor(secs / 60);
        showToast(`⏰ Pace Reminder: ${mins} minutes elapsed.`);
      }
    }

    function showToast(msg) {
      const toast = document.getElementById('reminderToast');
      if (toast) {
        toast.textContent = msg;
        toast.style.display = 'block';
        setTimeout(() => { toast.style.display = 'none'; }, 6000);
      }
    }

    function startTimer() {
      if (!timerRunning) {
        timerRunning = true;
        document.getElementById('timerToggleBtn').textContent = 'Pause';
        timerInterval = setInterval(() => {
          timerSeconds++;
          document.getElementById('timerDisplay').textContent = formatTime(timerSeconds);
          checkTimerSoundMilestones(timerSeconds);
        }, 1000);
      }
    }

    function pauseTimer() {
      timerRunning = false;
      document.getElementById('timerToggleBtn').textContent = 'Resume';
      clearInterval(timerInterval);
    }

    function toggleTimer() {
      if (timerRunning) pauseTimer();
      else startTimer();
    }

    function resetTimer() {
      pauseTimer();
      timerSeconds = 0;
      document.getElementById('timerDisplay').textContent = '00:00';
      document.getElementById('timerToggleBtn').textContent = 'Start';
    }

    /* ==========================================================================
       SYNTHESIZER AUDIO & REMINDER CHIME ENGINE
       ========================================================================== */
    let soundEnabled = true;
    let audioCtx = null;

    function getAudioContext() {
      if (!audioCtx) {
        const AudioClass = window.AudioContext || window.webkitAudioContext;
        if (AudioClass) audioCtx = new AudioClass();
      }
      if (audioCtx && audioCtx.state === 'suspended') {
        audioCtx.resume().catch(() => {});
      }
      return audioCtx;
    }

    function playSound(type) {
      if (!soundEnabled) return;
      try {
        const ctx = getAudioContext();
        if (!ctx) return;
        const now = ctx.currentTime;
        if (type === 'correct') {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = 'sine';
          osc.frequency.setValueAtTime(659.25, now);
          osc.frequency.exponentialRampToValueAtTime(880, now + 0.15);
          gain.gain.setValueAtTime(0.15, now);
          gain.gain.linearRampToValueAtTime(0.001, now + 0.25);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(now);
          osc.stop(now + 0.26);
        } else if (type === 'incorrect') {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = 'triangle';
          osc.frequency.setValueAtTime(196, now);
          osc.frequency.exponentialRampToValueAtTime(146, now + 0.18);
          gain.gain.setValueAtTime(0.15, now);
          gain.gain.linearRampToValueAtTime(0.001, now + 0.22);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(now);
          osc.stop(now + 0.24);
        }
      } catch(e) {}
    }

    /* Melodic Multi-Tone Reminder Chime for 20m and 5m intervals */
    function playReminderChime() {
      if (!soundEnabled) return;
      try {
        const ctx = getAudioContext();
        if (!ctx) return;
        const now = ctx.currentTime;
        const chimeNotes = [523.25, 659.25, 783.99, 1046.50]; // C5 - E5 - G5 - C6
        chimeNotes.forEach((freq, idx) => {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = 'sine';
          osc.frequency.setValueAtTime(freq, now + idx * 0.14);
          gain.gain.setValueAtTime(0.001, now + idx * 0.14);
          gain.gain.linearRampToValueAtTime(0.22, now + idx * 0.14 + 0.03);
          gain.gain.exponentialRampToValueAtTime(0.0001, now + idx * 0.14 + 0.65);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(now + idx * 0.14);
          osc.stop(now + idx * 0.14 + 0.7);
        });
      } catch(e) {}
    }

    /* ==========================================================================
       IN-MEMORY STATE MANAGEMENT
       ========================================================================== */
    let state = {
      currentProblemIdx: 0,
      problems: {}
    };

    function getProblemState(idx) {
      if (!state.problems[idx]) {
        state.problems[idx] = { completedSteps: [], inputs: {}, isSolved: false, isSkipped: false };
      }
      return state.problems[idx];
    }

    function cleanString(s) {
      return (s || "").toString().trim().toLowerCase().replace(/\s+/g, '').replace(/−/g, '-');
    }

    function testInputMatching(userStr, targetStr, altStr) {
      const u = cleanString(userStr);
      const t = cleanString(targetStr);
      if (!u) return false;
      if (u === t) return true;
      if (altStr) {
        const alts = altStr.split('|').map(cleanString);
        if (alts.includes(u)) return true;
      }
      
      const parseVal = (str) => {
        if (!str) return NaN;
        if (str.includes('/')) {
          const parts = str.split('/');
          return parts.length === 2 ? parseFloat(parts[0]) / parseFloat(parts[1]) : NaN;
        }
        return parseFloat(str);
      };
      const numU = parseVal(u);
      const numT = parseVal(t);
      if (!isNaN(numU) && !isNaN(numT)) {
        return Math.abs(numU - numT) < 0.02;
      }
      return false;
    }

    function triggerMathTypeset() {
      if (window.MathJax && typeof window.MathJax.typesetPromise === 'function') {
        window.MathJax.typesetPromise().catch(() => {});
      }
    }

    /* Keypad Helpers */
    let activeInputElement = null;
    window.trackActiveField = function(el) { activeInputElement = el; };
    window.insertSymbol = function(sym) {
      if (!activeInputElement) return;
      const start = activeInputElement.selectionStart || 0;
      const end = activeInputElement.selectionEnd || 0;
      const val = activeInputElement.value;
      activeInputElement.value = val.substring(0, start) + sym + val.substring(end);
      activeInputElement.focus();
      activeInputElement.dispatchEvent(new Event('input', { bubbles: true }));
    };
    window.clearActiveField = function() {
      if (!activeInputElement) return;
      activeInputElement.value = '';
      activeInputElement.dispatchEvent(new Event('input', { bubbles: true }));
      activeInputElement.focus();
    };

    window.switchToolTab = function(tab) {
      document.getElementById('tabPadBtn').classList.toggle('active', tab === 'pad');
      document.getElementById('tabCalcBtn').classList.toggle('active', tab === 'calc');
      document.getElementById('mathPadView').style.display = tab === 'pad' ? 'grid' : 'none';
      document.getElementById('calcView').style.display = tab === 'calc' ? 'block' : 'none';
    };

    let calcExpression = "";
    window.calcAppend = function(val) { calcExpression += val; document.getElementById('calcScreen').textContent = calcExpression || "0"; };
    window.calcClear = function() { calcExpression = ""; document.getElementById('calcScreen').textContent = "0"; };
    window.calcSqrt = function() {
      try { calcExpression = String(Math.sqrt(eval(calcExpression || "0"))); document.getElementById('calcScreen').textContent = calcExpression; } catch(e) {}
    };
    window.calcEval = function() {
      try { calcExpression = String(eval(calcExpression || "0")); document.getElementById('calcScreen').textContent = calcExpression; } catch(e) {}
    };

    /* Navigation */
    function switchMainTab(tabId) {
      document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
      const targetBtn = Array.from(document.querySelectorAll('.tab-btn')).find(b => b.getAttribute('onclick') && b.getAttribute('onclick').includes(tabId));
      if (targetBtn) targetBtn.classList.add('active');

      document.querySelectorAll('.view-section').forEach(sec => sec.classList.remove('active'));
      const targetSec = document.getElementById(`${tabId}View`);
      if (targetSec) targetSec.classList.add('active');
      window.scrollTo({ top: 0, behavior: 'smooth' });

      if (tabId === 'sheet') {
        renderProblem(state.currentProblemIdx);
        if (!timerRunning && timerSeconds === 0) startTimer();
      }
      if (tabId === 'solutions') renderSolutions();
      triggerMathTypeset();
    }

    function renderProblem(idx) {
      if (idx < 0 || idx >= PROBLEMS_DATA.length) return;
      state.currentProblemIdx = idx;
      const prob = PROBLEMS_DATA[idx];
      const pState = getProblemState(idx);

      document.getElementById('pNumberDisplay').textContent = prob.title;
      document.getElementById('pCategoryBadge').textContent = prob.category;
      document.getElementById('pPartsBadge').textContent = prob.partsInfo;
      document.getElementById('pContextDisplay').innerHTML = prob.context;

      const badge = document.getElementById('pStatusBadge');
      if (pState.isSolved) { badge.className = 'status-badge badge-complete'; badge.textContent = 'Completed'; }
      else if (pState.isSkipped) { badge.className = 'status-badge badge-skipped'; badge.textContent = 'Skipped'; }
      else if (pState.completedSteps.length > 0) { badge.className = 'status-badge badge-progress'; badge.textContent = 'In Progress'; }
      else { badge.className = 'status-badge badge-unvisited'; badge.textContent = 'Unvisited'; }

      const container = document.getElementById('stepsListContainer');
      container.innerHTML = '';

      const maxStep = pState.isSolved ? prob.steps.length - 1 : Math.min(pState.completedSteps.length, prob.steps.length - 1);

      for (let sIdx = 0; sIdx <= maxStep; sIdx++) {
        const step = prob.steps[sIdx];
        const isDone = pState.completedSteps.includes(sIdx);

        const card = document.createElement('div');
        card.className = `step-card ${isDone ? 'completed' : 'active'}`;
        card.innerHTML = `
          <div class="step-header-bar">
            <div class="step-title-text">${step.title}</div>
            <span class="step-status-indicator">${isDone ? '✓ Verified' : 'Current Step'}</span>
          </div>
          <div class="step-prompt">${step.prompt}</div>
          <div class="step-controls">
            <div></div>
            <div style="display:flex; align-items:center; gap:8px;">
              <span class="step-feedback-msg" id="step-msg-${idx}-${sIdx}"></span>
              ${!isDone ? `
                <button class="btn btn-step-check" onclick="verifyStepAnswers(${idx}, ${sIdx})">
                  ${sIdx === prob.steps.length - 1 ? 'Verify & Finish Problem ✓' : 'Verify & Continue →'}
                </button>
              ` : '<span style="color:var(--correct-green); font-weight:700;">✓ Correct</span>'}
            </div>
          </div>
        `;
        container.appendChild(card);

        card.querySelectorAll('.step-input').forEach((inp, iIdx) => {
          const inputKey = `p${idx}_s${sIdx}_i${iIdx}`;
          inp.setAttribute('data-key', inputKey);
          inp.setAttribute('onfocus', 'trackActiveField(this)');
          if (pState.inputs[inputKey] !== undefined) inp.value = pState.inputs[inputKey];

          if (isDone) {
            inp.disabled = true;
            inp.classList.add('input-correct');
          } else {
            inp.addEventListener('input', (e) => { pState.inputs[inputKey] = e.target.value; });
            inp.addEventListener('keypress', (e) => { if (e.key === 'Enter') verifyStepAnswers(idx, sIdx); });
          }
        });
      }

      document.getElementById('prevProblemBtn').disabled = idx === 0;
      document.getElementById('nextProblemBtn').disabled = idx === PROBLEMS_DATA.length - 1;
      renderPalette();
      triggerMathTypeset();
    }

    window.verifyStepAnswers = function(pIdx, sIdx) {
      const prob = PROBLEMS_DATA[pIdx];
      const pState = getProblemState(pIdx);
      const card = document.querySelectorAll('.step-card')[sIdx];
      if (!card) return;

      const inputs = card.querySelectorAll('.step-input');
      let ok = true;

      inputs.forEach(inp => {
        const ans = inp.getAttribute('data-ans') || '';
        const alt = inp.getAttribute('data-alt') || '';
        const inputKey = inp.getAttribute('data-key');
        pState.inputs[inputKey] = inp.value;

        if (testInputMatching(inp.value, ans, alt)) {
          inp.classList.remove('input-incorrect');
          inp.classList.add('input-correct');
        } else {
          inp.classList.remove('input-correct');
          inp.classList.add('input-incorrect');
          ok = false;
        }
      });

      const msg = document.getElementById(`step-msg-${pIdx}-${sIdx}`);
      if (ok) {
        playSound('correct');
        if (!pState.completedSteps.includes(sIdx)) pState.completedSteps.push(sIdx);
        pState.isSkipped = false;
        if (msg) {
          msg.className = "step-feedback-msg correct";
          msg.textContent = "✓ Correct!";
        }
        if (pState.completedSteps.length === prob.steps.length) {
          pState.isSolved = true;
          setTimeout(() => renderProblem(pIdx), 350);
        } else {
          setTimeout(() => renderProblem(pIdx), 300);
        }
      } else {
        playSound('incorrect');
        if (msg) {
          msg.className = "step-feedback-msg incorrect";
          msg.textContent = "✗ Check calculation and try again.";
        }
      }
    };

    function renderPalette() {
      const grid = document.getElementById('paletteGridContainer');
      grid.innerHTML = '';
      let solvedCount = 0;

      PROBLEMS_DATA.forEach((p, idx) => {
        const btn = document.createElement('button');
        btn.className = 'palette-btn';
        btn.textContent = p.id;
        const ps = state.problems[idx];
        if (ps) {
          if (ps.isSolved) { btn.classList.add('completed'); solvedCount++; }
          else if (ps.isSkipped) btn.classList.add('skipped');
          else if (ps.completedSteps.length > 0) btn.classList.add('progress');
        }
        if (idx === state.currentProblemIdx) btn.classList.add('active');
        btn.onclick = () => renderProblem(idx);
        grid.appendChild(btn);
      });
      document.getElementById('completionRateText').textContent = `${solvedCount}/${PROBLEMS_DATA.length} Solved`;
    }

    document.getElementById('prevProblemBtn').onclick = () => { if (state.currentProblemIdx > 0) renderProblem(state.currentProblemIdx - 1); };
    document.getElementById('nextProblemBtn').onclick = () => { if (state.currentProblemIdx < PROBLEMS_DATA.length - 1) renderProblem(state.currentProblemIdx + 1); };
    document.getElementById('skipProblemBtn').onclick = () => {
      const ps = getProblemState(state.currentProblemIdx);
      ps.isSkipped = true;
      if (state.currentProblemIdx < PROBLEMS_DATA.length - 1) renderProblem(state.currentProblemIdx + 1);
      else renderProblem(state.currentProblemIdx);
    };

    document.getElementById('finishAssessmentBtn').onclick = () => {
      pauseTimer();
      switchMainTab('solutions');
    };

    function renderSolutions() {
      let solved = 0, skipped = 0;
      PROBLEMS_DATA.forEach((p, idx) => {
        const ps = state.problems[idx];
        if (ps && ps.isSolved) solved++;
        else if (ps && ps.isSkipped) skipped++;
      });
      const total = PROBLEMS_DATA.length;
      document.getElementById('finalScoreVal').textContent = solved;
      document.getElementById('accuracyStat').textContent = `${Math.round((solved/total)*100)}%`;
      document.getElementById('correctCountStat').textContent = solved;
      document.getElementById('skippedCountStat').textContent = skipped;

      const desc = document.getElementById('performanceFeedbackDesc');
      desc.textContent = solved === total 
        ? `🌟 Outstanding mastery! You completed all 15 questions flawlessly in ${formatTime(timerSeconds)}.` 
        : `Completed in ${formatTime(timerSeconds)}. Review the step rationales below to master solving equations with variables on both sides.`;

      const container = document.getElementById('reviewListContainer');
      container.innerHTML = '';

      PROBLEMS_DATA.forEach((prob, idx) => {
        const card = document.createElement('div');
        card.className = 'review-card';
        let stepsHTML = prob.steps.map(st => `
          <div style="margin-top:10px; padding:12px; background:#f0f9ff; border-left:3px solid var(--primary-blue); border-radius:4px; border:1px solid var(--blue-border-soft); border-left-width:3px;">
            <strong style="color:var(--primary-dark); font-size:0.95rem;">${st.title}</strong>
            <p style="margin-top:4px; font-size:0.95rem; color:#0c4a6e;">${st.explanation}</p>
          </div>
        `).join('');
        card.innerHTML = `
          <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:0.5rem;">
            <strong style="color:var(--primary-dark); font-size:1.1rem;">${prob.title} (${prob.category})</strong>
            <span class="status-badge ${state.problems[idx]?.isSolved ? 'badge-complete' : 'badge-skipped'}">
              ${state.problems[idx]?.isSolved ? 'Solved' : 'Review'}
            </span>
          </div>
          <div style="font-size:1.05rem; margin-bottom:0.5rem;">${prob.context}</div>
          ${stepsHTML}
        `;
        container.appendChild(card);
      });
      triggerMathTypeset();
    }

    document.getElementById('retakeQuizBtn').onclick = () => {
      state.problems = {};
      state.currentProblemIdx = 0;
      resetTimer();
      switchMainTab('sheet');
    };

    document.getElementById('soundToggleBtn').onclick = () => {
      soundEnabled = !soundEnabled;
      document.getElementById('soundIcon').textContent = soundEnabled ? '🔊' : '🔇';
    };

    window.addEventListener('DOMContentLoaded', () => {
      renderProblem(0);
      triggerMathTypeset();
    });
  </script>
</body>
</html>
