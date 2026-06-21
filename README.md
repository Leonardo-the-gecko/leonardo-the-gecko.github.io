<!DOCTYPE html>
<html>
<head>
<title>Gecko Clicker</title>
<link rel="stylesheet" href="Geckoclicker.css">
<style>
    body {
        background: #E7CBA0;
        font-family: Arial, sans-serif;
        text-align: center;
        padding: 20px;
    }

    #gecko {
        width: 200px;
        cursor: pointer;
        transition: transform 0.1s;
        animation: spin 4s linear infinite;
        transform-style: preserve-3d;
    }

    #gecko:active {
        transform: scale(0.9);
    }

    @keyframes spin {
        0% { transform: rotateY(0deg); }
        100% { transform: rotateY(360deg); }
    }

    .shop {
        margin-top: 30px;
        background: #fff;
        padding: 20px;
        width: 350px;
        margin-left: auto;
        margin-right: auto;
        border-radius: 10px;
        box-shadow: 0 0 10px #0003;
    }

    button {
        width: 100%;
        padding: 10px;
        margin-top: 10px;
        font-size: 16px;
        cursor: pointer;
    }
</style>
</head>
<body>

<h1>Leo Clicker</h1>

<h2>Clicks: <span id="clicks">0</span></h2>
<h3>Clicks Per Second: <span id="cps">0</span></h3>

<img id="gecko" src="Geckoclickerimgs/blank.png">

<div class="shop">
    <h2>Upgrades</h2>

    <!-- Named upgrades -->
    <button onclick="buyClickUpgrade()">Finger Training (+1 CPC) — Cost: <span id='clickUpgradeCost'>20</span></button>
    <button onclick="buyCps1()">Mini Gecko Helper (+1 CPS) — Cost: <span id='cps1Cost'>50</span></button>
    <button onclick="buyCps100()">Gecko Army (+100 CPS) — Cost: <span id='cps100Cost'>500</span></button>

    <button onclick="buyClick10()">Protein Shake (+10 CPC) — Cost: <span id='click10Cost'>200</span></button>
    <button onclick="buyClick50()">Super Strength (+50 CPC) — Cost: <span id='click50Cost'>1000</span></button>

    <button onclick="buyCps10()">Gecko Squad (+10 CPS) — Cost: <span id='cps10Cost'>400</span></button>
    <button onclick="buyCps500()">Gecko Factory (+500 CPS) — Cost: <span id='cps500Cost'>5000</span></button>

    <button onclick="buyMegaFactory()">MEGA LEO INDUSTRIES (+5000 CPS) — Cost: <span id='megaFactoryCost'>50000</span></button>
</div>

<div class="shop">
    <h2>Skin Shop</h2>
    <div id="skinShop"></div>
</div>

<script>
    let clicks = 0;
    let clicksPerClick = 1;
    let cps = 0;

    let clickUpgradeCost = 20;
    let cps1Cost = 50;
    let cps100Cost = 500;

    let click10Cost = 200;
    let click50Cost = 1000;

    let cps10Cost = 400;
    let cps500Cost = 5000;

    let megaFactoryCost = 50000;

    document.getElementById("gecko").onclick = function() {
        clicks += clicksPerClick;
        updateDisplay();
    };

    function updateDisplay() {
        document.getElementById("clicks").innerText = clicks;
        document.getElementById("cps").innerText = cps;

        document.getElementById("clickUpgradeCost").innerText = clickUpgradeCost;
        document.getElementById("cps1Cost").innerText = cps1Cost;
        document.getElementById("cps100Cost").innerText = cps100Cost;

        document.getElementById("click10Cost").innerText = click10Cost;
        document.getElementById("click50Cost").innerText = click50Cost;

        document.getElementById("cps10Cost").innerText = cps10Cost;
        document.getElementById("cps500Cost").innerText = cps500Cost;

        document.getElementById("megaFactoryCost").innerText = megaFactoryCost;
    }

    /* Upgrade functions */
    function buyClickUpgrade() {
        if (clicks >= clickUpgradeCost) {
            clicks -= clickUpgradeCost;
            clicksPerClick += 1;
            clickUpgradeCost = Math.floor(clickUpgradeCost * 1.5);
            updateDisplay();
        }
    }

    function buyCps1() {
        if (clicks >= cps1Cost) {
            clicks -= cps1Cost;
            cps += 1;
            cps1Cost += 1;
            updateDisplay();
        }
    }

    function buyCps100() {
        if (clicks >= cps100Cost) {
            clicks -= cps100Cost;
            cps += 100;
            cps100Cost = Math.floor(cps100Cost * 1.5);
            updateDisplay();
        }
    }

    function buyClick10() {
        if (clicks >= click10Cost) {
            clicks -= click10Cost;
            clicksPerClick += 10;
            click10Cost = Math.floor(click10Cost * 1.5);
            updateDisplay();
        }
    }

    function buyClick50() {
        if (clicks >= click50Cost) {
            clicks -= click50Cost;
            clicksPerClick += 50;
            click50Cost = Math.floor(click50Cost * 1.5);
            updateDisplay();
        }
    }

    function buyCps10() {
        if (clicks >= cps10Cost) {
            clicks -= cps10Cost;
            cps += 10;
            cps10Cost = Math.floor(cps10Cost * 1.5);
            updateDisplay();
        }
    }

    function buyCps500() {
        if (clicks >= cps500Cost) {
            clicks -= cps500Cost;
            cps += 500;
            cps500Cost = Math.floor(cps500Cost * 1.5);
            updateDisplay();
        }
    }

    function buyMegaFactory() {
        if (clicks >= megaFactoryCost) {
            clicks -= megaFactoryCost;
            cps += 5000;
            megaFactoryCost = Math.floor(megaFactoryCost * 1.5);
            updateDisplay();
        }
    }

    /* Auto CPS */
    setInterval(() => {
        clicks += cps;
        updateDisplay();
    }, 1000);

    /* SKINS — added 10 new ones */
    const skins = [
        { id: "default", name: "Normal Leo", price: 0, img: "Geckoclickerimgs/blank.png", owned: true },
        { id: "topHat", name: "Top Hat Leo", price: 200, img: "Geckoclickerimgs/tophat.png", owned: false },
        { id: "banana", name: "Banana Leo", price: 500, img: "Geckoclickerimgs/Banana.png", owned: false },
        { id: "wizard", name: "Wizard Leo", price: 1200, img: "Geckoclickerimgs/wizard.png", owned: false },
        { id: "cowboy", name: "Cowboy Leo", price: 1500, img: "Geckoclickerimgs/cowboy.png", owned: false },
        { id: "viking", name: "Viking Leo", price: 2000, img: "Geckoclickerimgs/viking.png", owned: false },
        { id: "sunglasses", name: "Cool Shades Leo", price: 800, img: "Geckoclickerimgs/cool.png", owned: false },
        { id: "business", name: "BIGSHOT Leo", price: 2500, img: "Geckoclickerimgs/BIGSHOT.png", owned: false },
        { id: "angel", name: "Angel Leo", price: 3000, img: "Geckoclickerimgs/angel.png", owned: false },
        { id: "demon", name: "Devil Leo", price: 3500, img: "Geckoclickerimgs/devil.png", owned: false },
        { id: "party", name: "Party Leo", price: 1000, img: "Geckoclickerimgs/Party.png", owned: false },
        { id: "ninja", name: "Ninja Leo", price: 1800, img: "Geckoclickerimgs/ninja.png", owned: false },
        { id: "pirate", name: "Pirate Leo", price: 2200, img: "Geckoclickerimgs/pirate.png", owned: false },

        /* NEW SKINS */
        { id: "robot", name: "Robot Leo", price: 4000, img: "Geckoclickerimgs/robot.png", owned: false },
        { id: "gold", name: "Golden Leo", price: 6000, img: "Geckoclickerimgs/gold.png", owned: false },
        { id: "rainbow", name: "Rainbow Leo", price: 8000, img: "Geckoclickerimgs/rainbow.png", owned: false },
        { id: "samurai", name: "Samurai Leo", price: 5000, img: "Geckoclickerimgs/samurai.png", owned: false },
        { id: "alien", name: "Alien Leo", price: 7000, img: "Geckoclickerimgs/alien.png", owned: false },
        { id: "snow", name: "Snow Leo", price: 3500, img: "Geckoclickerimgs/snow.png", owned: false },
        { id: "fire", name: "Fire Leo", price: 7500, img: "Geckoclickerimgs/fire.png", owned: false },
        { id: "toxic", name: "Radiation Leo", price: 6500, img: "Geckoclickerimgs/toxic.png", owned: false },
        { id: "ghost", name: "Ghost Leo", price: 9000, img: "Geckoclickerimgs/ghost.png", owned: false },
        { id: "cyber", name: "Cyber Leo", price: 10000, img: "Geckoclickerimgs/cyber.png", owned: false }
    ];

    let equippedSkin = "default";

    function renderSkinShop() {
        const shop = document.getElementById("skinShop");
        shop.innerHTML = "";

        skins.forEach(skin => {
            const div = document.createElement("div");
            div.style.marginBottom = "15px";

            div.innerHTML = `
                <strong>${skin.name}</strong><br>
                <img src="${skin.img}" width="80"><br>
                ${skin.owned 
                    ? `<button onclick="equipSkin('${skin.id}')">Equip</button>`
                    : `<button onclick="buySkin('${skin.id}')">Buy (${skin.price} clicks)</button>`
                }
            `;

            shop.appendChild(div);
        });
    }

    function buySkin(id) {
        const skin = skins.find(s => s.id === id);

        if (clicks >= skin.price) {
            clicks -= skin.price;
            skin.owned = true;
            updateDisplay();
            renderSkinShop();
        }
    }

    function equipSkin(id) {
        const skin = skins.find(s => s.id === id);

        if (skin.owned) {
            equippedSkin = id;
            document.getElementById("gecko").src = skin.img;
        }
    }

    renderSkinShop();
</script>

</body>
</html>
