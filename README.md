<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Binance Box</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: black;
            color: yellow;
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .text {
            position: absolute;
            font-size: 24px;
            font-weight: bold;
            text-shadow: 0 0 10px yellow;
            animation: moveText 5s linear infinite;
        }

        .text.top {
            top: 10px;
            left: 50%;
            transform: translateX(-50%);
        }

        .text.bottom {
            bottom: 10px;
            left: 50%;
            transform: translateX(-50%);
        }

        @keyframes moveText {
            0% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(20px); }
            100% { transform: translateX(-50%) translateY(0); }
        }

        .gift {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            border-radius: 50%;
            animation: moveGift 5s linear infinite;
        }

        @keyframes moveGift {
            0% { transform: translate(0, 0); }
            25% { transform: translate(200px, 100px); }
            50% { transform: translate(400px, 0); }
            75% { transform: translate(200px, -100px); }
            100% { transform: translate(0, 0); }
        }

        .button {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            padding: 20px 40px;
            background-color: orange;
            color: black;
            border: 2px solid yellow;
            border-radius: 50px;
            font-size: 24px;
            cursor: pointer;
        }

        .modal {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: gray;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            z-index: 1000;
        }

        .modal button {
            margin: 10px;
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
        }

        .modal .close {
            position: absolute;
            top: 10px;
            left: 10px;
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
        }

        .modal .close:hover {
            color: red;
        }

        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: yellow;
            animation: confetti 2s linear infinite;
        }

        @keyframes confetti {
            0% { transform: translateY(0) rotate(0deg); }
            100% { transform: translateY(100vh) rotate(360deg); }
        }

        input[type="text"] {
            padding: 10px;
            font-size: 16px;
            width: 80%;
            margin-bottom: 10px;
            border: 2px solid yellow;
            border-radius: 5px;
            background-color: black;
            color: yellow;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="text top">Binance Box</div>
        <div class="text bottom">Binance Box</div>
        <div class="gift"></div>
        <button class="button" onclick="openModal()">Open Box</button>
    </div>

    <div id="modal" class="modal">
        <button class="close" onclick="closeModal()">←</button>
        <button onclick="showCongratulations()">Find Your Crypto Box</button>
    </div>

    <div id="congratulations" class="modal">
        <button class="close" onclick="closeCongratulations()">←</button>
        <h2>Congratulations!</h2>
        <p>You won 12 USDT</p>
        <button onclick="showClaim()">Claim Prize</button>
    </div>

    <div id="claim" class="modal">
        <button class="close" onclick="closeClaim()">←</button>
        <h2>Binance Box Congratulates You!</h2>
        <p>To claim your prize, share your referral link:</p>
        <input type="text" id="referralLink" value="https://www.rxminer.com/#/?ref=901664" readonly>
        <button onclick="copyLink()">Copy Link</button>
    </div>

    <script>
        function openModal() {
            document.getElementById('modal').style.display = 'block';
        }

        function closeModal() {
            document.getElementById('modal').style.display = 'none';
        }

        function showCongratulations() {
            document.getElementById('modal').style.display = 'none';
            document.getElementById('congratulations').style.display = 'block';
        }

        function closeCongratulations() {
            document.getElementById('congratulations').style.display = 'none';
        }

        function showClaim() {
            document.getElementById('congratulations').style.display = 'none';
            document.getElementById('claim').style.display = 'block';
        }

        function closeClaim() {
            document.getElementById('claim').style.display = 'none';
        }

        function copyLink() {
            const link = document.getElementById('referralLink');
            link.select();
            document.execCommand('copy');
            alert('Link copied to clipboard!');
        }

        // Gift animation
        const gifts = document.querySelectorAll('.gift');
        gifts.forEach(gift => {
            gift.addEventListener('animationiteration', () => {
                gift.style.backgroundColor = `rgb(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255})`;
                gift.style.transform = `scale(${Math.random() * 2 + 1})`;
            });
        });

        // Confetti animation
        setInterval(() => {
            const confetti = document.createElement('div');
            confetti.className = 'confetti';
            confetti.style.left = `${Math.random() * 100}vw`;
            confetti.style.backgroundColor = `rgb(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255})`;
            document.body.appendChild(confetti);
            setTimeout(() => confetti.remove(), 2000);
        }, 100);
    </script>
</body>
</html>
