<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Why Aerospace Engineering is the Ultimate Major</title>
  <style>
    /* CSS Custom Properties & Design System */
    :root {
      --bg-dark: #090d16;
      --bg-card: rgba(22, 30, 49, 0.65);
      --accent-blue: #38bdf8;
      --accent-indigo: #818cf8;
      --accent-cyan: #22d3ee;
      --text-main: #f8fafc;
      --text-muted: #94a3b8;
      --border-color: rgba(255, 255, 255, 0.1);
      --glass-border: rgba(56, 189, 248, 0.2);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      background-color: var(--bg-dark);
      color: var(--text-main);
      line-height: 1.6;
      background-image: 
        radial-gradient(circle at 15% 15%, rgba(56, 189, 248, 0.08) 0%, transparent 40%),
        radial-gradient(circle at 85% 85%, rgba(129, 140, 248, 0.08) 0%, transparent 40%);
      background-attachment: fixed;
      padding-bottom: 4rem;
    }

    /* Container Layout */
    .container {
      max-width: 1100px;
      margin: 0 auto;
      padding: 0 1.5rem;
    }

    /* Hero Section */
    header {
      padding: 5rem 0 3rem;
      text-align: center;
      position: relative;
    }

    .badge {
      display: inline-block;
      padding: 0.35rem 1rem;
      background: rgba(56, 189, 248, 0.1);
      border: 1px solid var(--glass-border);
      border-radius: 50px;
      color: var(--accent-blue);
      font-size: 0.85rem;
      font-weight: 600;
      letter-spacing: 1px;
      text-transform: uppercase;
      margin-bottom: 1.5rem;
    }

    h1 {
      font-size: clamp(2.2rem, 5vw, 3.8rem);
      font-weight: 800;
      line-height: 1.15;
      margin-bottom: 1.2rem;
      background: linear-gradient(135deg, #ffffff 30%, var(--accent-blue) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .hero-subtitle {
      font-size: 1.2rem;
      color: var(--text-muted);
      max-width: 700px;
      margin: 0 auto;
    }

    /* Stats Grid */
    .stats-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 1.5rem;
      margin: 3rem 0;
    }

    .stat-card {
      background: var(--bg-card);
      border: 1px solid var(--border-color);
      backdrop-filter: blur(12px);
      border-radius: 16px;
      padding: 1.5rem;
      text-align: center;
    }

    .stat-number {
      font-size: 2.2rem;
      font-weight: 700;
      color: var(--accent-cyan);
      margin-bottom: 0.25rem;
    }

    .stat-label {
      font-size: 0.9rem;
      color: var(--text-muted);
    }

    /* Section Styling */
    section {
      margin-top: 4rem;
    }

    h2 {
      font-size: 2rem;
      margin-bottom: 2rem;
      text-align: center;
      position: relative;
    }

    h2::after {
      content: '';
      display: block;
      width: 50px;
      height: 3px;
      background: var(--accent-blue);
      margin: 0.5rem auto 0;
      border-radius: 2px;
    }

    /* Grid Layout for Reasons */
    .reasons-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
    }

    .card {
      background: var(--bg-card);
      border: 1px solid var(--border-color);
      border-radius: 16px;
      padding: 2rem;
      backdrop-filter: blur(10px);
      transition: transform 0.3s ease, border-color 0.3s ease;
    }

    .card:hover {
      transform: translateY(-5px);
      border-color: var(--glass-border);
    }

    .card-icon {
      font-size: 2rem;
      margin-bottom: 1rem;
      display: inline-block;
    }

    .card h3 {
      font-size: 1.3rem;
      color: var(--text-main);
      margin-bottom: 0.75rem;
    }

    .card p {
      color: var(--text-muted);
      font-size: 0.95rem;
    }

    /* Callout Banner */
    .callout-box {
      margin-top: 4rem;
      background: linear-gradient(135deg, rgba(56, 189, 248, 0.1) 0%, rgba(129, 140, 248, 0.1) 100%);
      border: 1px solid var(--glass-border);
      border-radius: 20px;
      padding: 3rem 2rem;
      text-align: center;
    }

    .callout-box h3 {
      font-size: 1.8rem;
      margin-bottom: 1rem;
    }

    .callout-box p {
      color: var(--text-muted);
      max-width: 650px;
      margin: 0 auto 1.5rem;
    }

    .btn {
      display: inline-block;
      padding: 0.8rem 2rem;
      background: linear-gradient(135deg, var(--accent-blue), var(--accent-indigo));
      color: #fff;
      font-weight: 600;
      text-decoration: none;
      border-radius: 50px;
      box-shadow: 0 4px 15px rgba(56, 189, 248, 0.3);
      transition: opacity 0.2s ease;
    }

    .btn:hover {
      opacity: 0.9;
    }

    footer {
      text-align: center;
      margin-top: 5rem;
      color: var(--text-muted);
      font-size: 0.85rem;
    }
  </style>
</head>
<body>

  <div class="container">
    <header>
      <span class="badge">Major Spotlight</span>
      <h1>Why Aerospace Engineering is the Ultimate Field</h1>
      <p class="hero-subtitle">From designing next-generation atmospheric jets to engineering interplanetary spacecraft, aerospace is where human ambition meets cutting-edge physics.</p>
    </header>

    <!-- Industry Key Metrics -->
    <div class="stats-container">
      <div class="stat-card">
        <div class="stat-number">$134,830</div>
        <div class="stat-label">U.S. Median Annual Wage</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">~$800B</div>
        <div class="stat-label">Projected Global Space Economy</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">6%</div>
        <div class="stat-label">Projected 10-Yr Job Growth</div>
      </div>
    </div>

    <!-- Core Pillars -->
    <section>
      <h2>The Core Advantages</h2>
      <div class="reasons-grid">
        
        <div class="card">
          <div class="card-icon">🚀</div>
          <h3>Work on Epic Challenges</h3>
          <p>You aren't just optimizing software for clicks; you are building machines that defy gravity, survive atmospheric re-entry, and explore Mars. The scale and impact of your work are unmatched.</p>
        </div>

        <div class="card">
          <div class="card-icon">⚡</div>
          <h3>The Private Space Boom</h3>
          <p>With companies like SpaceX, Rocket Lab, and Blue Origin joining traditional defense giants and space agencies like NASA, the sector is experiencing unprecedented innovation and private funding.</p>
        </div>

        <div class="card">
          <div class="card-icon">🧠</div>
          <h3>Ultra-Versatile Skill Set</h3>
          <p>Aerospace pushes you to master fluid dynamics, structural integrity, thermodynamics, and guidance control. These rigorous fundamentals make you instantly valuable across automotive, energy, and tech roles.</p>
        </div>

        <div class="card">
          <div class="card-icon">💼</div>
          <h3>High Earning Potential</h3>
          <p>With starting salaries well above average and a high median pay, aerospace consistently rates as one of the most financially rewarding undergraduate engineering paths available.</p>
        </div>

        <div class="card">
          <div class="card-icon">🌍</div>
          <h3>Sustainable Futures</h3>
          <p>Modern aerospace isn't just about rockets—it's leading the charge toward green aviation, electric vertical takeoff and landing (eVTOL) crafts, and low-emission commercial flight.</p>
        </div>

        <div class="card">
          <div class="card-icon">✨</div>
          <h3>High Career Fulfillment</h3>
          <p>Few feelings rival watching something you helped design leave the launchpad or take flight for the first time. Aerospace engineers work on projects that define human history.</p>
        </div>

      </div>
    </section>

    <!-- Call to Action -->
    <div class="callout-box">
      <h3>Ready to Reach Orbit?</h3>
      <p>Aerospace engineering demands solid math and physics foundations, but the reward is a career building the future of flight and space exploration.</p>
      <a href="#learn-more" class="btn">Explore Degree Programs</a>
    </div>

    <footer>
      <p>Source Data: U.S. Bureau of Labor Statistics & Space Economy Projections.</p>
    </footer>
  </div>

</body>
</html>
