<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Rohen Clicker Site</title>

<style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: "Segoe UI", sans-serif; }

    body {
        min-height: 100vh;
        background: linear-gradient(120deg, #6a00ff, #00d4ff, #00ff9d);
        background-size: 300% 300%;
        animation: gradientShift 12s ease infinite;
        display: flex;
        flex-direction: column;
        align-items: center;
        overflow: hidden;
        padding-bottom: 200px;
    }

    @keyframes gradientShift {
        0% { background-position: 0% 50%; }
        50% { background-position: 100% 50%; }
        100% { background-position: 0% 50%; }
    }

    .title {
        font-size: 3rem;
        font-weight: 900;
        margin-top: 20px;
        background: linear-gradient(90deg, red, orange, yellow, green, cyan, blue, purple);
        background-size: 400% 400%;
        -webkit-background-clip: text;
        color: transparent;
        animation: chromaWave 6s linear infinite, wave 2s ease-in-out infinite;
        text-shadow: 0 0 20px rgba(255,255,255,0.4);
    }

    @keyframes chromaWave {
        0% { background-position: 0% 50%; }
        50% { background-position: 100% 50%; }
        100% { background-position: 0% 50%; }
    }

    @keyframes wave {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-10px); }
    }

    .stats-btn {
        position: fixed;
        top: 15px;
        right: 15px;
        padding: 10px 20px;
        background: rgba(255,255,255,0.25);
        border: 2px solid rgba(255,255,255,0.5);
        border-radius: 10px;
        color: white;
        cursor: pointer;
        font-size: 1rem;
        backdrop-filter: blur(10px);
        transition: 0.3s;
        z-index: 1000;
    }

    .stats-btn:hover {
        background: white;
        color: #6a00ff;
    }

    .stats-box {
        position: fixed;
        /* positioning context for the secret corner trigger */
        top: 60px;
        right: 15px;
        width: 250px;
        padding: 20px;
        background: rgba(0,0,0,0.55);
        border-radius: 15px;
        color: white;
        font-size: 1.1rem;
        display: none;
        z-index: 1000;
        backdrop-filter: blur(10px);
    }

    .floating-head {
        position: absolute;
        width: 80px;
        height: 80px;
        border-radius: 50%;
        animation: floatUp 2.2s ease-out forwards;
        pointer-events: none;
        z-index: 999;
    }

    @keyframes floatUp {
        0% { opacity: 1; transform: scale(1); }
        100% { opacity: 0; transform: scale(1.2); }
    }

    .clicker-container {
        margin-top: 40px;
        text-align: center;
        color: white;
    }

    .spawn-btn {
        padding: 15px 40px;
        font-size: 1.3rem;
        border-radius: 30px;
        border: 2px solid rgba(255,255,255,0.5);
        background: rgba(255,255,255,0.2);
        color: white;
        cursor: pointer;
        transition: 0.3s;
    }

    .spawn-btn:hover {
        background: white;
        color: #6a00ff;
        box-shadow: 0 0 20px white;
    }

    .score {
        font-size: 1.5rem;
    }

    .upgrade-row {
        margin-top: 25px;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 15px;
        justify-content: center;
    }

    .buy-buttons-row {
        display: flex;
        gap: 15px;
        flex-wrap: wrap;
        justify-content: center;
    }

    .upgrade-section-label {
        font-size: 1rem;
        font-weight: 700;
        letter-spacing: 0.5px;
        opacity: 0.85;
        text-transform: uppercase;
    }

    .upgrade-btn {
        padding: 10px 20px;
        background: rgba(255,255,255,0.15);
        border: 2px solid rgba(255,255,255,0.4);
        border-radius: 15px;
        cursor: pointer;
        color: white;
        display: flex;
        align-items: center;
        gap: 10px;
        transition: 0.3s;
    }

    .upgrade-btn:hover {
        background: white;
        color: #6a00ff;
        box-shadow: 0 0 20px white;
    }

    .upgrade-icon {
        width: 40px;
        height: 40px;
        border-radius: 10px;
    }

    .secret-trigger {
        position: absolute;
        bottom: 0;
        right: 0;
        width: 28px;
        height: 28px;
        background: transparent;
        border: none;
        cursor: default;
        padding: 0;
    }

    .secret-menu {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 300px;
        padding: 25px;
        background: rgba(0,0,0,0.85);
        border-radius: 15px;
        color: white;
        display: none;
        z-index: 2000;
        backdrop-filter: blur(10px);
        border: 2px solid rgba(255,255,255,0.3);
        text-align: center;
    }

    .secret-menu h3 {
        margin-bottom: 15px;
    }

    .secret-menu-close {
        margin-top: 15px;
        padding: 8px 18px;
        background: rgba(255,255,255,0.15);
        border: 2px solid rgba(255,255,255,0.4);
        border-radius: 12px;
        color: white;
        cursor: pointer;
    }

    .secret-menu-close:hover {
        background: white;
        color: #6a00ff;
    }

    .auto-rohen-display,
    .more-rohens-display {
        position: relative;
        width: 60px;
        height: 60px;
        margin: 15px auto 0;
        display: none;
    }

    .auto-rohen-display img,
    .more-rohens-display img {
        width: 60px;
        height: 60px;
        border-radius: 50%;
        object-fit: cover;
        border: 2px solid rgba(255,255,255,0.5);
        display: block;
    }

    .auto-rohen-badge,
    .more-rohens-badge {
        position: absolute;
        top: -6px;
        left: -6px;
        background: #ff2d55;
        color: white;
        font-size: 0.75rem;
        font-weight: 700;
        padding: 2px 6px;
        border-radius: 10px;
        border: 2px solid white;
        line-height: 1;
    }

    .owned-upgrades-row {
        display: flex;
        gap: 25px;
        justify-content: center;
        flex-wrap: wrap;
    }

    .version-tag {
        position: fixed;
        top: 15px;
        left: 15px;
        padding: 6px 12px;
        background: rgba(0,0,0,0.35);
        border-radius: 8px;
        color: rgba(255,255,255,0.75);
        font-size: 0.8rem;
        z-index: 1000;
        cursor: pointer;
        transition: 0.3s;
    }

    .version-tag:hover {
        background: rgba(0,0,0,0.55);
        color: white;
    }

    .version-box {
        position: fixed;
        top: 50px;
        left: 15px;
        padding: 15px 20px;
        background: rgba(0,0,0,0.55);
        border-radius: 15px;
        color: white;
        font-size: 1.1rem;
        display: none;
        z-index: 1000;
        backdrop-filter: blur(10px);
    }
</style>
</head>
<body>

<div class="version-tag" id="versionTag">v1.2.0</div>

<div class="version-box" id="versionBox">Made with love by 🦐</div>

<button class="stats-btn" id="statsBtn">Stats</button>

<div class="stats-box" id="statsBox">
    <div><b>All‑Time Rohens:</b> <span id="totalRohens">0</span></div>
    <div><b>Manual Rohens:</b> <span id="manualRohens">0</span></div>
    <div><b>Auto‑Rohens:</b> <span id="autoGenerated">0</span></div>
    <button class="secret-trigger" id="secretTrigger" aria-hidden="true" tabindex="-1"></button>
</div>

<div class="secret-menu" id="secretMenu">
    <h3>Secret Menu</h3>
    <div>You found it.</div>
    <button class="secret-menu-close" id="giveMillionButton" style="margin-top:15px;">Give 1,000,000 Rohens</button>
    <button class="secret-menu-close" id="secretMenuClose">Close</button>
</div>

<div class="title">SKCUS NEHOR</div>

<div class="clicker-container">
    <h2>Rohen Clicker</h2>

    <button id="clickButton" class="spawn-btn"><span id="scoreCount">0</span></button>

    <div class="upgrade-row">
        <div class="upgrade-section-label">More Rohens (+1/click)</div>
        <div class="buy-buttons-row">
            <button id="buyButton1xMore" class="upgrade-btn" disabled>
                <img src="RohenLibraries/IMG_6399.jpg" class="upgrade-icon">
                1x — Cost: <span id="cost1xMore">25</span>
            </button>

            <button id="buyButton10xMore" class="upgrade-btn" disabled>
                10x — Cost: <span id="cost10xMore">0</span>
            </button>

            <button id="buyButtonMaxMore" class="upgrade-btn" disabled>
                Max (<span id="maxCountMore">0</span>) — Cost: <span id="costMaxMore">0</span>
            </button>
        </div>
    </div>

    <div class="upgrade-row">
        <div class="upgrade-section-label">Auto‑Rohen (+1/sec)</div>
        <div class="buy-buttons-row">
            <button id="buyButton1x" class="upgrade-btn" disabled>
                <img src="RohenLibraries/IMG_6401.jpg" class="upgrade-icon">
                1x — Cost: <span id="cost1x">250</span>
            </button>

            <button id="buyButton10x" class="upgrade-btn" disabled>
                10x — Cost: <span id="cost10x">0</span>
            </button>

            <button id="buyButtonMax" class="upgrade-btn" disabled>
                Max (<span id="maxCount">0</span>) — Cost: <span id="costMax">0</span>
            </button>
        </div>
    </div>

    <div class="owned-upgrades-row">
        <div class="more-rohens-display" id="moreRohensDisplay">
            <span class="more-rohens-badge" id="moreRohensBadge">x0</span>
            <img src="RohenLibraries/IMG_6399.jpg" alt="More Rohens">
        </div>

        <div class="auto-rohen-display" id="autoRohenDisplay">
            <span class="auto-rohen-badge" id="autoRohenBadge">x0</span>
            <img src="RohenLibraries/IMG_6401.jpg" alt="Auto-Rohen">
        </div>
    </div>
</div>

<script>
    const clickButton = document.getElementById("clickButton");
    const scoreCount = document.getElementById("scoreCount");

    const buyButton1x = document.getElementById("buyButton1x");
    const buyButton10x = document.getElementById("buyButton10x");
    const buyButtonMax = document.getElementById("buyButtonMax");
    const cost1xDisplay = document.getElementById("cost1x");
    const cost10xDisplay = document.getElementById("cost10x");
    const maxCountDisplay = document.getElementById("maxCount");
    const costMaxDisplay = document.getElementById("costMax");
    const autoRohenDisplay = document.getElementById("autoRohenDisplay");
    const autoRohenBadge = document.getElementById("autoRohenBadge");

    const buyButton1xMore = document.getElementById("buyButton1xMore");
    const buyButton10xMore = document.getElementById("buyButton10xMore");
    const buyButtonMaxMore = document.getElementById("buyButtonMaxMore");
    const cost1xMoreDisplay = document.getElementById("cost1xMore");
    const cost10xMoreDisplay = document.getElementById("cost10xMore");
    const maxCountMoreDisplay = document.getElementById("maxCountMore");
    const costMaxMoreDisplay = document.getElementById("costMaxMore");
    const moreRohensDisplay = document.getElementById("moreRohensDisplay");
    const moreRohensBadge = document.getElementById("moreRohensBadge");

    const statsBtn = document.getElementById("statsBtn");
    const statsBox = document.getElementById("statsBox");

    const versionTag = document.getElementById("versionTag");
    const versionBox = document.getElementById("versionBox");

    const secretTrigger = document.getElementById("secretTrigger");
    const secretMenu = document.getElementById("secretMenu");
    const secretMenuClose = document.getElementById("secretMenuClose");
    const giveMillionButton = document.getElementById("giveMillionButton");

    const totalRohensDisplay = document.getElementById("totalRohens");
    const manualRohensDisplay = document.getElementById("manualRohens");
    const autoGeneratedDisplay = document.getElementById("autoGenerated");

    let score = 0;

    // Auto-Rohen upgrade
    const AUTO_SCALING = 1.02;
    let autoClicks = 0;
    let autoUpgradeCost = 250;

    // More Rohens upgrade — adds +1 Rohen per manual click for every level owned
    const MORE_ROHENS_SCALING = 1.01;
    let moreRohensCount = 0;
    let moreRohensCost = 25;
    let clickPower = 1;

    let totalRohens = 0;
    let manualRohens = 0;
    let autoRohensGenerated = 0;

    statsBtn.addEventListener("click", () => {
        statsBox.style.display = statsBox.style.display === "none" ? "block" : "none";
    });

    versionTag.addEventListener("click", () => {
        versionBox.style.display = versionBox.style.display === "none" ? "block" : "none";
    });

    secretTrigger.addEventListener("click", () => {
        secretMenu.style.display = "block";
    });

    secretMenuClose.addEventListener("click", () => {
        secretMenu.style.display = "none";
    });

    giveMillionButton.addEventListener("click", () => {
        score += 1000000;
        totalRohens += 1000000;

        scoreCount.textContent = score;
        totalRohensDisplay.textContent = totalRohens;

        updateBuyUI();
    });

    const MAX_HEADS = 30;
    let activeHeadCount = 0;

    function spawnHead() {
        if (activeHeadCount >= MAX_HEADS) return;
        activeHeadCount++;

        const head = document.createElement("img");
        head.src = "RohenLibraries/IMG_6400.jpg";
        head.classList.add("floating-head");

        const x = Math.random() * window.innerWidth;
        const y = Math.random() * window.innerHeight;

        head.style.left = x + "px";
        head.style.top = y + "px";

        document.body.appendChild(head);
        setTimeout(() => {
            head.remove();
            activeHeadCount--;
        }, 2200);
    }

    // Manual clicks always play the sound. Auto-Rohens play it more rarely
    // the more auto-generators you own, so a big auto army doesn't turn into
    // a wall of noise. With 1 auto-generator it plays ~1/3 of the time; with
    // 2 it's ~1/6, with 3 it's ~1/9, and so on (1 / (3 * autoClicks)).
    function playSound(isAuto = false) {
        if (isAuto) {
            const chance = 1 / (3 * autoClicks);
            if (Math.random() >= chance) return;
        }

        const s = new Audio("RohenLibraries/RohenHello.mp3");
        s.volume = Math.random() * (1.0 - 0.11) + 0.11;
        s.play();
    }

    function generateRohen(isAuto = false) {
        // Auto-Rohens always tick 1 at a time; manual clicks scale with
        // the "More Rohens" upgrade.
        const amount = isAuto ? 1 : clickPower;

        score += amount;
        totalRohens += amount;

        if (isAuto) {
            autoRohensGenerated += amount;
            autoGeneratedDisplay.textContent = autoRohensGenerated;
        } else {
            manualRohens += amount;
            manualRohensDisplay.textContent = manualRohens;
        }

        scoreCount.textContent = score;
        totalRohensDisplay.textContent = totalRohens;

        spawnHead();
        playSound(isAuto);

        updateBuyUI();
    }

    clickButton.addEventListener("click", () => generateRohen(false));

    // Applies price scaling to a cost, guaranteeing the price always goes
    // up by at least 1 even when `cost * scaling` rounds back down to the
    // same number (e.g. 25 * 1.01 = 25.25, which floors to 25 unchanged).
    function nextCost(cost, scaling) {
        return Math.max(cost + 1, Math.ceil(cost * scaling));
    }

    // Cost of buying `n` upgrades in a row from `startCost`, accounting for
    // the given price scaling on each one — without mutating any state,
    // just for display/afford-checks.
    function exactCost(startCost, scaling, n) {
        let cost = startCost;
        let total = 0;
        for (let i = 0; i < n; i++) {
            total += cost;
            cost = nextCost(cost, scaling);
        }
        return total;
    }

    // How many upgrades the current score can afford in a row starting from
    // `startCost`, and the total cost of doing so (used for "Max" buttons).
    function calcAffordable(startCost, scaling, available) {
        let cost = startCost;
        let total = 0;
        let count = 0;
        let remaining = available;

        while (remaining >= cost) {
            remaining -= cost;
            total += cost;
            count++;
            cost = nextCost(cost, scaling);
        }

        return { count, total };
    }

    function updateBuyUI() {
        // Auto-Rohen buttons
        const autoCost10 = exactCost(autoUpgradeCost, AUTO_SCALING, 10);
        const autoAffordable = calcAffordable(autoUpgradeCost, AUTO_SCALING, score);

        cost1xDisplay.textContent = autoUpgradeCost;
        cost10xDisplay.textContent = autoCost10;
        maxCountDisplay.textContent = autoAffordable.count;
        costMaxDisplay.textContent = autoAffordable.total;

        buyButton1x.disabled = score < autoUpgradeCost;
        buyButton10x.disabled = score < autoCost10;
        buyButtonMax.disabled = autoAffordable.count === 0;

        // More Rohens buttons
        const moreCost10 = exactCost(moreRohensCost, MORE_ROHENS_SCALING, 10);
        const moreAffordable = calcAffordable(moreRohensCost, MORE_ROHENS_SCALING, score);

        cost1xMoreDisplay.textContent = moreRohensCost;
        cost10xMoreDisplay.textContent = moreCost10;
        maxCountMoreDisplay.textContent = moreAffordable.count;
        costMaxMoreDisplay.textContent = moreAffordable.total;

        buyButton1xMore.disabled = score < moreRohensCost;
        buyButton10xMore.disabled = score < moreCost10;
        buyButtonMaxMore.disabled = moreAffordable.count === 0;
    }

    function afterAutoPurchase() {
        scoreCount.textContent = score;

        autoRohenDisplay.style.display = "block";
        autoRohenBadge.textContent = "x" + autoClicks;

        updateBuyUI();
    }

    function afterMoreRohensPurchase() {
        scoreCount.textContent = score;

        moreRohensDisplay.style.display = "block";
        moreRohensBadge.textContent = "x" + moreRohensCount;

        updateBuyUI();
    }

    // Buys exactly `n` auto-Rohens (all-or-nothing) if affordable.
    function buyFixedAuto(n) {
        const cost = exactCost(autoUpgradeCost, AUTO_SCALING, n);
        if (score < cost) return;

        score -= cost;
        for (let i = 0; i < n; i++) {
            autoUpgradeCost = nextCost(autoUpgradeCost, AUTO_SCALING);
        }
        autoClicks += n;

        afterAutoPurchase();
    }

    // Buys as many auto-Rohens as the current score allows.
    function buyMaxAuto() {
        const affordable = calcAffordable(autoUpgradeCost, AUTO_SCALING, score);
        if (affordable.count === 0) return;

        score -= affordable.total;
        for (let i = 0; i < affordable.count; i++) {
            autoUpgradeCost = nextCost(autoUpgradeCost, AUTO_SCALING);
        }
        autoClicks += affordable.count;

        afterAutoPurchase();
    }

    // Buys exactly `n` More Rohens levels (all-or-nothing) if affordable.
    function buyFixedMoreRohens(n) {
        const cost = exactCost(moreRohensCost, MORE_ROHENS_SCALING, n);
        if (score < cost) return;

        score -= cost;
        for (let i = 0; i < n; i++) {
            moreRohensCost = nextCost(moreRohensCost, MORE_ROHENS_SCALING);
        }
        moreRohensCount += n;
        clickPower = 1 + moreRohensCount;

        afterMoreRohensPurchase();
    }

    // Buys as many More Rohens levels as the current score allows.
    function buyMaxMoreRohens() {
        const affordable = calcAffordable(moreRohensCost, MORE_ROHENS_SCALING, score);
        if (affordable.count === 0) return;

        score -= affordable.total;
        for (let i = 0; i < affordable.count; i++) {
            moreRohensCost = nextCost(moreRohensCost, MORE_ROHENS_SCALING);
        }
        moreRohensCount += affordable.count;
        clickPower = 1 + moreRohensCount;

        afterMoreRohensPurchase();
    }

    buyButton1x.addEventListener("click", () => buyFixedAuto(1));
    buyButton10x.addEventListener("click", () => buyFixedAuto(10));
    buyButtonMax.addEventListener("click", () => buyMaxAuto());

    buyButton1xMore.addEventListener("click", () => buyFixedMoreRohens(1));
    buyButton10xMore.addEventListener("click", () => buyFixedMoreRohens(10));
    buyButtonMaxMore.addEventListener("click", () => buyMaxMoreRohens());

    updateBuyUI();

    setInterval(() => {
        if (autoClicks > 0) {
            for (let i = 0; i < autoClicks; i++) {
                generateRohen(true);
            }
        }
    }, 1000);
</script>

</body>
</html>
