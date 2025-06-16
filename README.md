<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>For My Love</title>
  <style>
    body {
      background-color: #000;
      color: #fff;
      font-family: 'Arial', sans-serif;
      text-align: center;
      padding: 20px;
      overflow: hidden;
    }
    .music-box {
      background-color: #d94f68;
      padding: 10px;
      border-radius: 10px;
      display: inline-block;
      margin-bottom: 20px;
      z-index: 2;
      position: relative;
    }
    .music-box p {
      margin: 0;
      font-weight: bold;
    }
    .carousel {
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      width: 250px;
      height: 250px;
      margin: 0 auto 20px;
      border-radius: 10px;
      position: relative;
      z-index: 2;
    }
    .carousel img {
      width: 100%;
      height: auto;
      border-radius: 10px;
      display: none;
      position: absolute;
    }
    .carousel img.active {
      display: block;
    }
    .timer {
      font-size: 1.2em;
      margin-bottom: 10px;
      z-index: 2;
      position: relative;
    }
    .message {
      max-width: 600px;
      margin: auto;
      font-size: 1.1em;
      line-height: 1.6;
      z-index: 2;
      position: relative;
    }
    .heart {
      color: #ff4d6d;
    }

    /* Floating Hearts */
    .hearts {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
      overflow: hidden;
      pointer-events: none;
    }
    .hearts span {
      position: absolute;
      display: block;
      font-size: 20px;
      color: #ff4d6d;
      animation: float 10s linear infinite;
      opacity: 0.6;
    }
    @keyframes float {
      0% {
        transform: translateY(100vh) scale(1);
        opacity: 0;
      }
      50% {
        opacity: 1;
      }
      100% {
        transform: translateY(-10vh) scale(1.2);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <div class="hearts">
    <!-- Generate floating hearts -->
    <script>
      for (let i = 0; i < 30; i++) {
        let heart = document.createElement('span');
        heart.innerText = '♥';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDelay = Math.random() * 5 + 's';
        heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
        document.querySelector('.hearts').appendChild(heart);
      }
    </script>
  </div>

  <div class="music-box">
    <p>♥ When I Met You - APO Hiking Society ♥</p>
    <audio controls autoplay loop>
      <source src="when-i-met-you.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
  </div>

  <!-- Carousel -->
  <div class="carousel" id="carousel">
    <img src="photo1.jpg" alt="Photo 1" class="active">
    <img src="photo2.jpg" alt="Photo 2">
    <img src="photo3.jpg" alt="Photo 3">
  </div>

  <div class="timer" id="loveTimer">
    ♥ Mi loveyyyy wewongggg for: ♥ <br>
    <span id="timeDisplay"></span>
  </div>

  <div class="message">
    <p>HAPPY 30th MONTHSARY MI LOVEYYYY we've been through a lot jd, we became strong in the lowest days and happy in the highest days thank you for being in my life, being genuine, caring, loving, supportive, and faithful to me. I pray for more years in our relationship until were old. I LOVEYYYYYY YOUUUU ALWAYSSSSS, MWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAMWAAAAAAAAA!! <span class="heart">♥</span></p>
  </div>

  <script>
    // Timer - 4 years, 6 months ago
    const startDate = new Date();
    startDate.setFullYear(startDate.getFullYear() - 2);
    startDate.setMonth(startDate.getMonth() - 6);
startDate.setDate(startDate.getDate() - (startDate.getDate() - 2));

    function updateTimer() {
      const now = new Date();
      const diff = now - startDate;

      const totalDays = Math.floor(diff / (1000 * 60 * 60 * 24));
      const years = Math.floor(totalDays / 365);
      const months = Math.floor((totalDays % 365) / 30);
      const days = totalDays - years * 365 - months * 30;
      const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutes = Math.floor((diff / (1000 * 60)) % 60);
      const seconds = Math.floor((diff / 1000) % 60);

      document.getElementById("timeDisplay").innerText =
        `${years} years, ${months} months, ${days} days, ${hours} hours, ${minutes} minutes and ${seconds} seconds`;
    }

    setInterval(updateTimer, 1000);
    updateTimer();

    // Carousel
    const images = document.querySelectorAll(".carousel img");
    let current = 0;

    function showNextImage() {
      images[current].classList.remove("active");
      current = (current + 1) % images.length;
      images[current].classList.add("active");
    }

    setInterval(showNextImage, 3000); // Change image every 3 seconds
  </script>
</body>
</html>
