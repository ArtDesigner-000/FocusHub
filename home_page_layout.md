<!DOCTYPE html>
<html>
<lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Focus Hub</title>
  <style>
    /* ===== General Styles ===== */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', sans-serif;
    }

    body {
      background-color: #121212;
      color: #fff;
    }

    a {
      text-decoration: none;
      color: inherit;
      cursor: pointer;
    }

    /* ===== Sidebar ===== */
    .sidebar {
      width: 220px;
      height: 100vh;
      background-color: #1E1E1E;
      position: fixed;
      top: 0;
      left: 0;
      display: flex;
      flex-direction: column;
      padding: 20px;
      gap: 15px;
    }

    .sidebar .logo {
      font-weight: bold;
      font-size: 20px;
      margin-bottom: 30px;
      color: #FFC107;
    }

    .sidebar a {
      padding: 10px 15px;
      border-radius: 8px;
      transition: background 0.2s;
    }

    .sidebar a:hover {
      background-color: #333;
    }

    /* ===== Main Content ===== */
    .main {
      margin-left: 240px;
      padding: 20px;
    }

    .greeting {
      font-size: 28px;
      margin-bottom: 5px;
    }

    .date {
      color: #aaa;
      font-size: 14px;
      margin-bottom: 20px;
    }

    /* ===== Info Cards ===== */
    .cards {
      display: flex;
      gap: 20px;
      margin-bottom: 30px;
    }

    .card {
      flex: 1;
      background-color: #1E1E1E;
      padding: 20px;
      border-radius: 12px;
      text-align: center;
    }

    .card .number {
      font-size: 32px;
      font-weight: bold;
      margin: 10px 0;
    }

    .card .label {
      color: #aaa;
      font-size: 14px;
    }

    /* ===== Daily Goals ===== */
    .daily-goals {
      background-color: #1E1E1E;
      padding: 20px;
      border-radius: 12px;
      margin-bottom: 30px;
    }

    .daily-goals h3 {
      margin-bottom: 15px;
    }

    .progress-bar {
      background-color: #333;
      border-radius: 10px;
      overflow: hidden;
      margin-bottom: 15px;
      height: 20px;
    }

    .progress {
      height: 100%;
      width: 0%;
      background-color: #FFC107;
      transition: width 0.5s;
    }

    /* ===== Quick Access ===== */
    .quick-access {
      display: flex;
      gap: 15px;
      flex-wrap: wrap;
    }

    .quick-access button {
      flex: 1 1 120px;
      padding: 15px;
      border: none;
      border-radius: 12px;
      background-color: #333;
      color: #fff;
      cursor: pointer;
      font-size: 14px;
      transition: background 0.2s;
    }

    .quick-access button:hover {
      background-color: #555;
    }
  </style>
</head>
<body>
  <!-- Sidebar -->
  <div class="sidebar">
    <div class="logo">Zenith Focus</div>
    <a onclick="showSection('home')">Home</a>
    <a onclick="showSection('focus')">Focus Timer</a>
    <a onclick="showSection('tasks')">Tasks</a>
    <a onclick="showSection('notes')">Notes</a>
    <a onclick="showSection('methods')">Methods</a>
    <a onclick="showSection('ai')">AI Chat</a>
    <a onclick="showSection('progress')">Progress</a>
    <a onclick="showSection('achievements')">Achievements</a>
    <a onclick="showSection('hobbies')">Hobbies</a>
    <a onclick="showSection('chill')">Chill Zone</a>
    <button style="margin-top:auto;">Lock In</button>
  </div>

  <!-- Main Content -->
  <div class="main">
    <div id="home-section">
      <div class="greeting">Good afternoon 👋</div>
      <div class="date" id="date"></div>

      <div class="cards">
        <div class="card">
          <div class="label">Total XP</div>
          <div class="number" id="xp">0</div>
        </div>
        <div class="card">
          <div class="label">Streak</div>
          <div class="number" id="streak">0d</div>
        </div>
        <div class="card">
          <div class="label">Badges</div>
          <div class="number" id="badges">0/12</div>
        </div>
      </div>

      <div class="daily-goals">
        <h3>⚡ Daily Goals</h3>
        <div>Focus Time</div>
        <div class="progress-bar"><div class="progress" id="focus-progress"></div></div>
        <div>Tasks Done</div>
        <div class="progress-bar"><div class="progress" id="tasks-progress"></div></div>
      </div>

      <div class="quick-access">
        <button>Focus Timer</button>
        <button>Tasks</button>
        <button>Notes</button>
        <button>Methods</button>
      </div>
    </div>

    <!-- Placeholder sections -->
    <div id="focus-section" style="display:none;">Focus Timer Section</div>
    <div id="tasks-section" style="display:none;">Tasks Section</div>
    <div id="notes-section" style="display:none;">Notes Section</div>
    <div id="methods-section" style="display:none;">Methods Section</div>
    <div id="ai-section" style="display:none;">AI Chat Section</div>
    <div id="progress-section" style="display:none;">Progress Section</div>
    <div id="achievements-section" style="display:none;">Achievements Section</div>
    <div id="hobbies-section" style="display:none;">Hobbies Section</div>
    <div id="chill-section" style="display:none;">Chill Zone Section</div>
  </div>

  <script>
    // Display current date
    const date = new Date();
    const options = { weekday: 'long', month: 'long', day: 'numeric' };
    document.getElementById('date').innerText = date.toLocaleDateString(undefined, options);

    // Sidebar link functionality
    function showSection(section) {
      const sections = ['home', 'focus', 'tasks', 'notes', 'methods', 'ai', 'progress', 'achievements', 'hobbies', 'chill'];
      sections.forEach(s => {
        const elem = document.getElementById(s + '-section');
        if (s === section) {
          elem.style.display = 'block';
        } else {
          elem.style.display = 'none';
        }
      });
    }

    // Sample progress bars (just for demo)
    document.getElementById('focus-progress').style.width = '25%';
    document.getElementById('tasks-progress').style.width = '40%';
  </script>
</body>
</html>
