# Fermilab Environmental Monitoring Portal

Welcome to the live environmental dashboard for **Fermi National Accelerator Laboratory** (Batavia/Aurora, IL). Whether you are walking the grounds near Wilson Hall, monitoring outdoor conditions for site maintenance, or taking a break around the bison pasture, this portal gives you real-time visibility into local air conditions.

---

<style>
  :root {
    --bg: #0d1117;
    --card-bg: #161b22;
    --border: #30363d;
    --text: #f0f6fc;
    --text-muted: #8b949e;
    --accent: #58a6ff;
    --good: #3fb950;
    --moderate: #d29922;
  }

  .dashboard-wrapper {
    background-color: var(--bg);
    color: var(--text);
    padding: 1.5rem;
    border-radius: 12px;
    border: 1px solid var(--border);
    margin: 1.5rem 0;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  }

  .dashboard {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }

  .dashboard header {
    border-bottom: 1px solid var(--border);
    padding-bottom: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .dashboard header h2 { font-size: 1.25rem; font-weight: 600; margin: 0; color: var(--text); border: none; padding: 0; }
  .dashboard header span { color: var(--text-muted); font-size: 0.875rem; }

  .hero-card {
    background-color: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.5rem;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
    align-items: center;
  }

  .aqi-score {
    text-align: center;
    padding-right: 1.5rem;
    border-right: 1px solid var(--border);
  }

  .aqi-number {
    font-size: 4rem;
    font-weight: 800;
    color: var(--good);
    line-height: 1;
  }

  .aqi-status {
    display: inline-block;
    margin-top: 0.5rem;
    padding: 0.25rem 0.75rem;
    background: rgba(63, 185, 80, 0.15);
    color: var(--good);
    border-radius: 20px;
    font-weight: 600;
    font-size: 0.875rem;
  }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }

  .stat-box {
    background: rgba(255, 255, 255, 0.03);
    padding: 0.75rem;
    border-radius: 8px;
    border: 1px solid var(--border);
  }

  .stat-box .label { font-size: 0.75rem; color: var(--text-muted); }
  .stat-box .value { font-size: 1.125rem; font-weight: 600; margin-top: 0.25rem; color: var(--text); }

  .chart-card {
    background-color: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.5rem;
  }

  .chart-card h3 { font-size: 0.95rem; margin: 0 0 1rem 0; color: var(--text-muted); border: none; }

  .bars {
    display: flex;
    align-items: flex-end;
    gap: 0.5rem;
    height: 120px;
    padding-top: 1rem;
  }

  .bar-container {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
    height: 100%;
    justify-content: flex-end;
  }

  .bar {
    width: 100%;
    background-color: var(--accent);
    border-radius: 4px 4px 0 0;
  }

  .time { font-size: 0.7rem; color: var(--text-muted); }

  @media (max-width: 600px) {
    .hero-card { grid-template-columns: 1fr; }
    .aqi-score { border-right: none; border-bottom: 1px solid var(--border); padding-bottom: 1.5rem; padding-right: 0; }
  }
</style>

<div class="dashboard-wrapper">
  <div class="dashboard">
    <header>
      <div>
        <h2>Fermilab Air Quality</h2>
        <span>Batavia / Aurora, IL</span>
      </div>
      <span>Live Sync</span>
    </header>

    <div class="hero-card">
      <div class="aqi-score">
        <div class="aqi-number">40</div>
        <div class="aqi-status">Good Air Quality</div>
      </div>
      <div class="stats-grid">
        <div class="stat-box">
          <div class="label">PM2.5</div>
          <div class="value">7.3 µg/m³</div>
        </div>
        <div class="stat-box">
          <div class="label">Ground Ozone (O₃)</div>
          <div class="value">28 ppb</div>
        </div>
        <div class="stat-box">
          <div class="label">Humidity</div>
          <div class="value">57%</div>
        </div>
        <div class="stat-box">
          <div class="label">Wind</div>
          <div class="value">7 km/h</div>
        </div>
      </div>
    </div>

    <div class="chart-card">
      <h3>Today's AQI Trend (Batavia Area)</h3>
      <div class="bars">
        <div class="bar-container"><div class="bar" style="height: 35%; background: var(--good);"></div><span class="time">08:00</span></div>
        <div class="bar-container"><div class="bar" style="height: 40%; background: var(--good);"></div><span class="time">10:00</span></div>
        <div class="bar-container"><div class="bar" style="height: 52%; background: var(--good);"></div><span class="time">12:00</span></div>
        <div class="bar-container"><div class="bar" style="height: 40%; background: var(--good);"></div><span class="time">14:00</span></div>
        <div class="bar-container"><div class="bar" style="height: 37%; background: var(--good);"></div><span class="time">16:00</span></div>
        <div class="bar-container"><div class="bar" style="height: 35%; background: var(--good);"></div><span class="time">18:00</span></div>
      </div>
    </div>
  </div>
</div>

---

## 1. Understanding the Air Quality Index (AQI)

The **Air Quality Index (AQI)** is a standardized scale run by the EPA that runs from **0 to 500**. It measures how clean or polluted the air is and tells you what potential health impacts to expect.

| AQI Level | Category | What It Means |
|---|---|---|
| **0 – 50** | **Good (Green)** | Air quality is satisfactory; air pollution poses little or no risk. |
| **51 – 100** | **Moderate (Yellow)** | Air quality is acceptable, but unusually sensitive individuals may experience mild irritation. |
| **101 – 150** | **Unhealthy for Sensitive Groups (Orange)** | Members of sensitive groups (e.g., asthma, heart conditions) may experience health effects. |
| **151 – 200** | **Unhealthy (Red)** | Everyone may begin to experience adverse health effects; sensitive groups experience more serious effects. |
| **201 – 300+** | **Very Unhealthy / Hazardous (Purple/Maroon)** | Health alert: emergency conditions where the entire population is likely to be affected. |

---

## 2. Key Local Pollutants

Air quality around Northern Illinois is primarily influenced by two key pollutants:

* **Fine Particulate Matter (PM2.5):** Tiny airborne particles (less than 2.5 micrometers in diameter—about 30 times smaller than a human hair) caused by combustion, vehicle exhaust, and regional agricultural activity. Because they are so small, they can bypass the nose and throat to penetrate deep into the lungs.
* **Ground-Level Ozone (O3):** Unlike the protective ozone layer high in the stratosphere, ground-level ozone is created at surface level when sunlight reacts with industrial emissions and vehicular exhaust, especially on hot summer afternoons.

---

## 3. Health & Exposure Guidelines

> **Current Campus Condition:** With the current AQI sitting comfortably in the **Good (0–50)** range, the air poses **no health risk** for outdoor activity on campus.

When air quality dips into higher tiers, standard health precautions apply:

* **Moderate (51–100):** Unusually sensitive individuals should consider limiting prolonged outdoor exertion if experiencing coughing or throat irritation.
* **Unhealthy for Sensitive Groups (101–150):** Children, elderly adults, and people with respiratory diseases (like asthma) should take frequent breaks and avoid heavy outdoor exertion.
* **Unhealthy (151+):** All individuals should reduce prolonged or heavy exertion outdoors and consider staying indoors in filtered, air-conditioned spaces.
