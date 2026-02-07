<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Love Animation</title>

<style>
body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f5f5f5;
    overflow: hidden;
    font-family: Arial, sans-serif;
}

.container {
    position: relative;
    width: 400px;
    height: 350px;
}

.heart {
    position: absolute;
    width: 20px;
    height: 20px;
    background: red;
    transform: rotate(45deg);
    animation: float 3s ease forwards;
}

.heart::before,
.heart::after {
    content: "";
    position: absolute;
    width: 20px;
    height: 20px;
    background: red;
    border-radius: 50%;
}

.heart::before {
    top: -10px;
    left: 0;
}

.heart::after {
    left: -10px;
    top: 0;
}

@keyframes float {
    from {
        transform: translateY(200px) rotate(45deg);
        opacity: 0;
    }
    to {
        transform: translateY(0) rotate(45deg);
        opacity: 1;
    }
}

.text {
    position: absolute;
    bottom: -40px;
    width: 100%;
    text-align: center;
    font-size: 32px;
    color: crimson;
    opacity: 0;
    animation: showText 2s ease forwards;
    animation-delay: 3s;
}

@keyframes showText {
    to {
        opacity: 1;
    }
}
</style>
</head>

<body>

<div class="container" id="love"></div>
<div class="text">I Love You ❤️</div>

<script>
const container = document.getElementById("love");

for (let t = 0; t < Math.PI * 2; t += 0.2) {

    let x = 200 + 120 * Math.pow(Math.sin(t), 3);
    let y = 150 - (
        70 * Math.cos(t)
        - 30 * Math.cos(2 * t)
        - 10 * Math.cos(3 * t)
        - 5 * Math.cos(4 * t)
    );

    let heart = document.createElement("div");
    heart.className = "heart";
    heart.style.left = x + "px";
    heart.style.top = y + "px";

    container.appendChild(heart);
}
</script>

</body>
</html>
