<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <title>Papatyalar Açıyor</title>
  <style>
    body {
      margin: 0;
      background: #000; /* Siyah arka plan */
      height: 100vh;
      overflow: hidden;
      font-family: sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }

    #touchButton {
      padding: 15px 30px;
      font-size: 20px;
      border: none;
      border-radius: 10px;
      background-color: #ffcf33;
      color: #000;
      cursor: pointer;
      box-shadow: 0 4px 6px rgba(255,255,255,0.4);
      transition: 0.3s ease;
      z-index: 10;
    }

    #touchButton:hover {
      background-color: #ffe066;
    }

    #treeContainer {
      position: absolute;
      bottom: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
    }

    .tree {
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 20px;
      height: 0;
      background-color: #4b2e18;
      animation: growTree 2s ease-out forwards;
    }

    @keyframes growTree {
      to {
        height: 250px;
      }
    }

    .flower {
      width: 40px;
      height: 40px;
      position: absolute;
      background: radial-gradient(circle at center, white 70%, yellow 30%);
      border-radius: 50%;
      opacity: 0;
      transform: scale(0.1);
      animation: bloom 0.6s ease-out forwards;
    }

    @keyframes bloom {
      to {
        opacity: 1;
        transform: scale(1);
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

      // Ağaç
      const tree = document.createElement("div");
      tree.classList.add("tree");
      treeContainer.appendChild(tree);

      // Ağaç büyüdükten sonra çiçekleri çıkar
      setTimeout(() => {
        const flowerCount = 12;
        for (let i = 0; i < flowerCount; i++) {
          const flower = document.createElement("div");
          flower.classList.add("flower");

          const offsetX = (Math.random() - 0.5) * 150;
          const offsetY = i * 20 + 60;

          flower.style.left = `calc(50% + ${offsetX}px)`;
          flower.style.bottom = `${offsetY}px`;
          flower.style.animationDelay = `${i * 0.2}s`;

          treeContainer.appendChild(flower);
        }
      }, 2000); // Ağaç animasyonu süresi kadar bekle
    });
  </script>

</body>
</html>
