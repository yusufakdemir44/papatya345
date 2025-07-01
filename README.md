<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <title>Papatyalar Açıyor</title>
  <style>
    body {
      margin: 0;
      background: #cce7ff;
      height: 100vh;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      font-family: 'Segoe UI', sans-serif;
    }

    #touchButton {
      padding: 15px 30px;
      font-size: 20px;
      border: none;
      border-radius: 10px;
      background-color: #ffcf33;
      color: #333;
      cursor: pointer;
      box-shadow: 0 4px 6px rgba(0,0,0,0.2);
      transition: all 0.3s ease;
      z-index: 10;
    }

    #touchButton:hover {
      background-color: #ffda66;
    }

    #treeContainer {
      position: absolute;
      bottom: 0;
      width: 100%;
      height: 100%;
      overflow: visible;
    }

    .tree {
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 20px;
      height: 0;
      background-color: #4b2e18;
      animation: growTree 2s ease-in-out forwards;
    }

    @keyframes growTree {
      0% {
        height: 0;
      }
      100% {
        height: 200px;
      }
    }

    .flower {
      width: 40px;
      height: 40px;
      background: radial-gradient(circle, white 60%, yellow 30%);
      border-radius: 50%;
      position: absolute;
      opacity: 0;
      animation: bloom 1s ease forwards;
    }

    @keyframes bloom {
      0% {
        transform: scale(0.2);
        opacity: 0;
      }
      100% {
        transform: scale(1);
        opacity: 1;
      }
    }
  </style>
</head>
<body>

  <button id="touchButton">🌼 Dokun</button>
  <div id="treeContainer"></div>

  <script>
    const button = document.getElementById("touchButton");
    const treeContainer = document.getElementById("treeContainer");

    button.addEventListener("click", () => {
      button.style.display = "none";

      // Ağaç oluştur
      const tree = document.createElement("div");
      tree.classList.add("tree");
      treeContainer.appendChild(tree);

      // Ağaç büyüme süresi kadar bekle
      setTimeout(() => {
        // Çiçekler ekle
        const flowerCount = 10;
        for (let i = 0; i < flowerCount; i++) {
          const flower = document.createElement("div");
          flower.classList.add("flower");

          const offsetX = (Math.random() - 0.5) * 200;
          const offsetY = i * 18 + 50;

          flower.style.left = `calc(50% + ${offsetX}px)`;
          flower.style.bottom = `${offsetY}px`;
          flower.style.animationDelay = `${i * 0.3}s`;

          treeContainer.appendChild(flower);
        }
      }, 2000); // Ağacın büyüme animasyonu süresi
    });
  </script>

</body>
</html>

