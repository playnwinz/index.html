# index.html
<!DOCTYPE html>
<html>
<head>
  <title>Spinner Game</title>
  <style>
    #wheel {
      width: 300px;
      height: 300px;
      border: 10px solid #333;
      border-radius: 50%;
      margin: 50px auto;
      position: relative;
    }
    #spinBtn {
      display: block;
      margin: 20px auto;
      padding: 10px 20px;
      font-size: 18px;
    }
    .result {
      text-align: center;
      font-size: 24px;
    }
  </style>
</head>
<body>
  <h1 style="text-align:center;">Spinner Game</h1>
  <div id="wheel"></div>
  <button id="spinBtn">Spin</button>
  <div class="result" id="result"></div>

  <script>
    const wheel = document.getElementById('wheel');
    const result = document.getElementById('result');
    let isSpinning = false;

    document.getElementById('spinBtn').addEventListener('click', () => {
      if (isSpinning) return;
      isSpinning = true;
      const prize = ["10 Points", "20 Points", "Try Again", "50 Points", "0 Points", "100 Points"];
      const angle = Math.floor(Math.random() * 360 + 720); // Spin at least 2 times
      wheel.style.transition = 'transform 4s ease-out';
      wheel.style.transform = `rotate(${angle}deg)`;

      setTimeout(() => {
        const final = Math.floor((angle % 360) / 60);
        result.innerText = "You got: " + prize[final];
        isSpinning = false;
      }, 4000);
    });
  </script>
</body>
</html>
