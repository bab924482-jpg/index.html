<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>لعبة صائد النجوم - ذوالفقار</title>
    <style>
        body { margin: 0; overflow: hidden; background: #2c3e50; font-family: Arial, sans-serif; touch-action: none; }
        #gameCanvas { display: block; background: #1a1a2e; }
        #ui { position: absolute; top: 10px; left: 10px; color: white; font-size: 20px; pointer-events: none; }
        #msg { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); 
               color: #f1c40f; font-size: 30px; text-align: center; display: none; }
    </style>
</head>
<body>

<div id="ui">النقاط: <span id="score">0</span></div>
<div id="msg">انتهى الوقت!<br><button onclick="location.reload()" style="padding:10px 20px; font-size:20px;">العب مرة ثانية</button></div>
<canvas id="gameCanvas"></canvas>

<script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');
    const scoreElement = document.getElementById('score');
    const msg = document.getElementById('msg');

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    let score = 0;
    let gameActive = true;
    let star = { x: Math.random() * (canvas.width - 50), y: Math.random() * (canvas.height - 50), size: 40 };

    function drawStar() {
        ctx.fillStyle = '#f1c40f';
        ctx.beginPath();
        ctx.arc(star.x + 20, star.y + 20, star.size / 2, 0, Math.PI * 2);
        ctx.fill();
        ctx.closePath();
    }

    function update() {
        if (!gameActive) return;
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        drawStar();
        requestAnimationFrame(update);
    }

    canvas.addEventListener('touchstart', (e) => {
        if (!gameActive) return;
        const touch = e.touches[0];
        const dist = Math.hypot(touch.clientX - (star.x + 20), touch.clientY - (star.y + 20));
        
        if (dist < star.size) {
            score++;
            scoreElement.innerText = score;
            star.x = Math.random() * (canvas.width - 50);
            star.y = Math.random() * (canvas.height - 50);
        }
    });

    // تنتهي اللعبة بعد 30 ثانية
    setTimeout(() => {
        gameActive = false;
        msg.style.display = 'block';
    }, 30000);

    update();
</script>

</body>
</html>
