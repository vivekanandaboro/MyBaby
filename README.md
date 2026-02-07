<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>My Question ❤️</title>

<style>
    body {
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background: linear-gradient(135deg, #ff9a9e, #fad0c4);
        font-family: Arial, sans-serif;
        overflow: hidden;
        text-align: center;
    }

    .box {
        background: white;
        padding: 40px 60px;
        border-radius: 20px;
        box-shadow: 0 15px 40px rgba(0,0,0,0.2);
    }

    h1 {
        color: #ff4d6d;
        margin-bottom: 30px;
    }

    button {
        font-size: 20px;
        padding: 12px 35px;
        margin: 10px;
        border-radius: 30px;
        border: none;
        cursor: pointer;
        transition: 0.2s;
    }

    #yesBtn {
        background: #ff4d6d;
        color: white;
    }

    #noBtn {
        background: #555;
        color: white;
        position: absolute;
    }

    .celebrate {
        font-size: 26px;
        color: #ff4d6d;
        margin-top: 20px;
        display: none;
    }
</style>
</head>

<body>

<div class="box">
    <h1>Will you be with me forever? ❤️</h1>
    <button id="yesBtn">Yes 💖</button>
    <button id="noBtn">No 😢</button>

    <div class="celebrate" id="msg">
       Happy Rose day my Baby I love you So much ummmmmhhhhhhhhhaaaaaa ❤️
    </div>
</div>

<!-- Music -->
<audio id="song">
   <source src="https://raw.githubusercontent.com/vivekanandaboro/Proposal-music/refs/heads/main/KINGH.mp3" type="audio/mp3">
</audio>

<script>
const yesBtn = document.getElementById("yesBtn");
const noBtn = document.getElementById("noBtn");
const song = document.getElementById("song");
const msg = document.getElementById("msg");

/* YES button */
yesBtn.onclick = () => {
    msg.style.display = "block";
    song.play();
    createHearts();
};

/* NO button runs away */
document.addEventListener("mousemove", (e) => {
    const rect = noBtn.getBoundingClientRect();

    const distance = Math.hypot(
        e.clientX - (rect.left + rect.width/2),
        e.clientY - (rect.top + rect.height/2)
    );

    if (distance < 100) {
        const x = Math.random() * (window.innerWidth - 100);
        const y = Math.random() * (window.innerHeight - 50);
        noBtn.style.left = x + "px";
        noBtn.style.top = y + "px";
    }
});

/* Floating hearts animation */
function createHearts() {
    setInterval(() => {
        const heart = document.createElement("div");
        heart.innerHTML = "❤️";
        heart.style.position = "absolute";
        heart.style.left = Math.random() * window.innerWidth + "px";
        heart.style.top = window.innerHeight + "px";
        heart.style.fontSize = "24px";

        document.body.appendChild(heart);

        let pos = window.innerHeight;
        const anim = setInterval(() => {
            pos -= 3;
            heart.style.top = pos + "px";

            if (pos < -20) {
                clearInterval(anim);
                heart.remove();
            }
        }, 20);
    }, 200);
}
</script>

</body>

</html>
