<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Be My Valentine 💘</title>

<style>
    body {
        margin: 0;
        height: 100vh;
        font-family: 'Segoe UI', sans-serif;
        background: linear-gradient(135deg, #ff758c, #ff7eb3);
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
    }

    .page {
        display: none;
        text-align: center;
        padding: 20px;
    }

    .active {
        display: block;
    }

    h1 {
        font-size: 2.2em;
    }

    button {
        padding: 15px 30px;
        font-size: 1.1em;
        border: none;
        border-radius: 30px;
        cursor: pointer;
        margin: 10px;
    }

    #yesBtn {
        background: #ff2e63;
        color: white;
    }

    #noBtn {
        background: #333;
        color: white;
        position: absolute;
    }

    .kiss {
        font-size: 2.8em;
        animation: float 2s infinite ease-in-out;
    }

    @keyframes float {
        0% { transform: translateY(0); }
        50% { transform: translateY(-20px); }
        100% { transform: translateY(0); }
    }

    .heart {
        position: absolute;
        font-size: 24px;
        animation: hearts 4s linear infinite;
    }

    @keyframes hearts {
        0% { opacity: 1; transform: translateY(0) scale(1); }
        100% { opacity: 0; transform: translateY(-300px) scale(1.8); }
    }
</style>
</head>

<body>

<!-- PAGE 1 -->
<div class="page active" id="page1">
    <h1>Will you be my Valentine? 💖</h1>
    <button id="yesBtn">YES 💘</button>
    <button id="noBtn">NO 🙄</button>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
    <div class="kiss">💋💋💋</div>

    <h1>Leticia Fafa Anku, I’m so lucky to have you 😘</h1>

    <p style="font-size:1.2em;">
        You are incredibly beautiful 😍  
        Thank you for being my Valentine ❤️  
        You mean the world to me 🌹
    </p>

    <div class="kiss">💋💋💋</div>
</div>

<!-- Romantic Music -->
<audio id="loveSong" loop>
    <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_7e8bb63d11.mp3" type="audio/mpeg">
</audio>

<script>
    const noBtn = document.getElementById("noBtn");
    const yesBtn = document.getElementById("yesBtn");
    const page1 = document.getElementById("page1");
    const page2 = document.getElementById("page2");
    const song = document.getElementById("loveSong");

    function moveButton() {
        const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
        const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
        noBtn.style.left = x + "px";
        noBtn.style.top = y + "px";
    }

    noBtn.addEventListener("mouseover", moveButton);
    noBtn.addEventListener("click", moveButton);
    moveButton();

    yesBtn.addEventListener("click", () => {
        page1.classList.remove("active");
        page2.classList.add("active");
        song.play();
        startHearts();
    });

    function startHearts() {
        setInterval(() => {
            const heart = document.createElement("div");
            heart.className = "heart";
            heart.textContent = "❤️";
            heart.style.left = Math.random() * window.innerWidth + "px";
            heart.style.bottom = "0px";
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 4000);
        }, 400);
    }
</script>

</body>
</html>
