<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gacha Game</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #222;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    #quiz {
      text-align: center;
    }
    button {
      margin: 10px;
      padding: 10px 20px;
      border: none;
      border-radius: 6px;
      background: #46a5ad;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background: #368b91;
    }
  </style>
</head>
<body>
  <div id="quiz">
    <h1>Câu hỏi</h1>
    <p id="question">Bạn đã sẵn sàng quay thưởng chưa?</p>
    <button onclick="showReward()">Quay Thưởng</button>
  </div>

  <script>
    // 🎁 Hiệu ứng mở hộp có âm thanh
    function showReward() {
      const overlay = document.createElement("div");
      overlay.style.position = "fixed";
      overlay.style.top = "0";
      overlay.style.left = "0";
      overlay.style.width = "100%";
      overlay.style.height = "100%";
      overlay.style.background = "rgba(0,0,0,0.9)";
      overlay.style.display = "flex";
      overlay.style.flexDirection = "column";
      overlay.style.alignItems = "center";
      overlay.style.justifyContent = "center";
      overlay.style.zIndex = 9999;

      // ✅ 2 ảnh phần thưởng
      const rewards = [
        "https://drive.google.com/uc?export=view&id=1V9TA6v_vKU5LmvoqlZjKy0xNqC5wmYrw",
        "https://drive.google.com/uc?export=view&id=1IJB9l6a_saKiSYlU96eLuNl5VzCr8fdH"
      ];

      // khung băng chuyền
      const frame = document.createElement("div");
      frame.style.width = "600px";
      frame.style.height = "150px";
      frame.style.overflow = "hidden";
      frame.style.border = "4px solid gold";
      frame.style.borderRadius = "12px";
      frame.style.background = "#111";
      frame.style.position = "relative";

      // băng chuyền
      const carousel = document.createElement("div");
      carousel.style.display = "flex";
      carousel.style.gap = "10px";
      carousel.style.position = "absolute";
      carousel.style.left = "0";
      carousel.style.top = "20px";
      carousel.style.transition = "transform 4s cubic-bezier(0.25, 1, 0.5, 1)";

      // thêm 20 ảnh random
      for (let i = 0; i < 20; i++) {
        const img = document.createElement("img");
        img.src = rewards[Math.floor(Math.random() * rewards.length)];
        img.style.width = "120px";
        img.style.height = "120px";
        img.style.objectFit = "cover";
        img.style.borderRadius = "8px";
        carousel.appendChild(img);
      }

      frame.appendChild(carousel);

      // pointer đỏ
      const pointer = document.createElement("div");
      pointer.style.position = "absolute";
      pointer.style.top = "0";
      pointer.style.left = "50%";
      pointer.style.transform = "translateX(-50%)";
      pointer.style.width = "4px";
      pointer.style.height = "150px";
      pointer.style.background = "red";
      frame.appendChild(pointer);

      document.body.appendChild(overlay);
      overlay.appendChild(frame);

      // âm thanh (cần có file sounds/tick.mp3 và sounds/win.mp3)
      const tickSound = new Audio("sounds/tick.mp3");
      const winSound = new Audio("sounds/win.mp3");

      // chạy âm tick khi băng chuyền
      let loop = true;
      setTimeout(() => {
        carousel.style.transform = "translateX(-1400px)";
        const tickLoop = setInterval(() => {
          if (!loop) clearInterval(tickLoop);
          tickSound.currentTime = 0;
          tickSound.play();
        }, 100);
      }, 100);

      // dừng sau 4.2s
      setTimeout(() => {
        loop = false;
        winSound.play();

        const msg = document.createElement("h2");
        msg.textContent = "🎉 Bạn nhận được phần thưởng!";
        msg.style.color = "gold";
        msg.style.marginTop = "20px";
        overlay.appendChild(msg);

        const btn = document.createElement("button");
        btn.textContent = "Đóng";
        btn.onclick = () => overlay.remove();
        overlay.appendChild(btn);
      }, 4200);
    }
  </script>
</body>
</html>
