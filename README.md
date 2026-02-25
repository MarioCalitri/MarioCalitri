👋 Ahoy! I’m Mario
Future Mobile App Developer™ | Bulldog Peacekeeper | LEGO Pirate Admiral | Code Wrangler
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Funny Coding Animation</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --bg: #0f1226;
      --panel: #191d3a;
      --text: #e6e6f0;
      --accent: #8ef6ff;
      --muted: #9aa3b2;
      --success: #74d99f;
      --warn: #ffc857;
      --error: #ff6b6b;
    }

    * { box-sizing: border-box; }
    body {
      margin: 0;
      min-height: 100vh;
      background: radial-gradient(1200px 600px at 70% 20%, #1b2048 10%, var(--bg) 60%);
      color: var(--text);
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji", "Segoe UI Emoji";
      display: grid;
      place-items: center;
      padding: 24px;
    }

    .stage {
      width: min(900px, 92vw);
      background: #111428aa;
      border: 1px solid #2a2f57;
      border-radius: 14px;
      overflow: hidden;
      backdrop-filter: blur(6px);
      box-shadow: 0 10px 40px #00000099, inset 0 0 0 1px #5c63b018;
    }

    .toolbar {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 12px 16px;
      background: linear-gradient(180deg, #1a1e3c, #131735);
      border-bottom: 1px solid #2a2f57;
    }
    .dot { width: 10px; height: 10px; border-radius: 50%; }
    .dot.red { background: #ff5f56; }
    .dot.yellow { background: #ffbd2e; }
    .dot.green { background: #27c93f; }
    .title {
      margin-left: auto;
      color: #c6cbff;
      font-size: 14px;
      letter-spacing: .2px;
      opacity: .9;
    }

    .content {
      display: grid;
      grid-template-columns: 1.2fr 1fr;
      gap: 16px;
      padding: 16px;
    }

    .editor, .console {
      background: var(--panel);
      border: 1px solid #2a2f57;
      border-radius: 10px;
      padding: 14px;
      position: relative;
      overflow: hidden;
    }

    .editor pre, .console pre {
      margin: 0;
      white-space: pre-wrap;
      word-break: break-word;
      font-family: SFMono-Regular, Menlo, Consolas, "Liberation Mono", monospace;
      font-size: 13.5px;
      line-height: 1.5;
      color: #d7dbff;
    }

    .gutter {
      position: absolute;
      top: 0; left: 0;
      bottom: 0;
      width: 44px;
      padding: 14px 8px;
      background: #171b38;
      color: #6f79a6;
      border-right: 1px solid #2a2f57;
      text-align: right;
      font-family: SFMono-Regular, Menlo, Consolas, monospace;
      font-size: 12px;
      line-height: 1.5;
      user-select: none;
    }

    .code {
      margin-left: 44px;
      animation: caret 1s steps(1) infinite;
      border-right: 2px solid transparent;
    }
    @keyframes caret {
      0%, 49%   { border-right-color: var(--accent); }
      50%, 100% { border-right-color: transparent; }
    }

    .status {
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 12.5px;
      color: var(--muted);
      margin-bottom: 8px;
    }
    .pulse {
      --c: var(--accent);
      width: 10px; height: 10px; border-radius: 50%;
      background: var(--c);
      box-shadow: 0 0 10px var(--c), 0 0 20px color-mix(in srgb, var(--c), transparent 30%);
      animation: pulse 1.6s ease-in-out infinite;
    }
    @keyframes pulse {
      0% { transform: scale(0.9); opacity: 0.7; }
      50% { transform: scale(1.15); opacity: 1; }
      100% { transform: scale(0.9); opacity: 0.7; }
    }

    /* The Bug 🐞 */
    .bug {
      position: absolute;
      top: 60%;
      left: -60px;
      font-size: 30px;
      filter: drop-shadow(0 4px 6px #0008);
      cursor: pointer;
      user-select: none;
      animation: scuttle 10s linear infinite;
    }
    @keyframes scuttle {
      0%   { transform: translateX(0) rotate(0deg); }
      20%  { transform: translateX(25vw) rotate(8deg); }
      40%  { transform: translateX(50vw) rotate(-6deg); }
      60%  { transform: translateX(70vw) rotate(6deg); }
      80%  { transform: translateX(85vw) rotate(-4deg); }
      100% { transform: translateX(105vw) rotate(0deg); }
    }
    .splat {
      animation: splat 350ms ease forwards;
    }
    @keyframes splat {
      0%   { transform: scale(1) rotate(0deg); filter: saturate(1); }
      80%  { transform: scale(1.5) rotate(12deg); filter: saturate(1.4); }
      100% { transform: scale(0) rotate(-12deg); filter: saturate(0.6); opacity: 0; }
    }

    /* Floating tips */
    .tip {
      position: absolute;
      font-size: 12px;
      color: #cbd3ff;
      background: #252b57d9;
      border: 1px solid #3a4396aa;
      padding: 6px 10px;
      border-radius: 8px;
      transform: translateY(-6px);
      animation: bob 2.6s ease-in-out infinite;
      pointer-events: none;
      backdrop-filter: blur(4px);
      box-shadow: 0 6px 18px #0006;
    }
    @keyframes bob {
      0%, 100% { transform: translateY(-6px); }
      50%      { transform: translateY(4px); }
    }

    /* Console styles */
    .console .line { margin: 2px 0; }
    .console .info { color: var(--accent); }
    .console .ok   { color: var(--success); }
    .console .warn { color: var(--warn); }
    .console .err  { color: var(--error); }
    .console .muted{ color: var(--muted); }

    /* Footer */
    .footer {
      padding: 10px 14px 14px;
      color: #aeb5df;
      font-size: 12px;
      opacity: .8;
      text-align: center;
    }

    /* Responsive */
    @media (max-width: 800px) {
      .content { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
  <div class="stage">
    <div class="toolbar">
      <span class="dot red"></span>
      <span class="dot yellow"></span>
      <span class="dot green"></span>
      <span class="title">coding-sesh.js — VS Code</span>
    </div>

    <div class="content">
      <!-- Editor Panel -->
      <section class="editor">
        <div class="gutter" id="gutter"></div>
        <pre class="code" id="code"></pre>
        <div class="tip" style="top:16px; right: 16px;">Tip: Click the 🐞 to squash the bug!</div>
        <div class="bug" id="bug" title="Click me!">🐞</div>
      </section>

      <!-- Console Panel -->
      <section class="console">
        <div class="status">
          <span class="pulse" style="--c: var(--accent)"></span>
          <span>Running build…</span>
        </div>
        <pre id="console">
<span class="muted">// output</span>
        </pre>
      </section>
    </div>

    <div class="footer">
      “It works on my machine” — every developer, moments before a demo. 🚀
    </div>
  </div>

  <script>
    // --- Typewriter effect in the "editor"
    const lines = [
`function fixBug() {`,
`  // TODO: figure out why it only fails on Fridays`,
`  const worksOnMyMachine = Math.random() > 0.5;`,
`  if (!worksOnMyMachine) {`,
`    throw new Error("It’s Friday, isn’t it?");`,
`  }`,
`  return "Ship it!";`,
`}`,
``,
`try {`,
`  console.log(fixBug());`,
`} catch (e) {`,
`  console.error("Bug found:", e.message);`,
`}`
    ];

    const codeEl = document.getElementById('code');
    const gutterEl = document.getElementById('gutter');
    const consoleEl = document.getElementById('console');

    // Render line numbers
I’m currently studying Mobile App Development at Trios College, where I spend my days learning how to convince code to behave and my nights Googling why it didn’t.

📱 What I’m Building (or Breaking)

Crafting mobile apps that work on both Android and iOS (on a good day)
Experimenting with UI/UX so my layouts stop looking like discount marketplace apps
Slowly mastering Git without accidentally deleting the universe
Expanding my debugging superpowers — currently at Level 2 (Level 3 unlocks patience)


🧱 Outside the Coding Mines
When I’m not battling a rogue semicolon, I'm probably:

🧱 Expanding my LEGO pirate fleet (the living room is now “The High Seas”)
🐶 Negotiating ceasefires between my two American Bulldogs
🔥 Pretending to be a Michelin chef on the Big Green Egg (BBQ/smoker)
📺 Doing very important “research” — mostly movies and TV shows


🧠 Philosophy I Code By
“If all else fails, stay calm and ask the All‑Seeing Eye (AI).”
It judges me less than my IDE.

💻 Tools I’m Learning to Tame

Git & GitHub (commit messages still chaotic but improving… maybe)
UX/UI - Figma
Co-pilot
and much much more to follow!


⚠️ Repo Disclaimer
Browse anything you like —
just please ignore the commit messages.
Yes, “fixed stuff again” is a valid message.
No, I will not elaborate.
And no, I will not apologize.

🚀 Want to Connect?
Open to collaboration, feedback, or LEGO pirate ship recommendations.
(Seriously. Always open to pirate ships.)
