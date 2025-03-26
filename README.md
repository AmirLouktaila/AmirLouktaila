<h2 align="left">Hi 👋! My name is salah, from algeria</h2>

<img height="150" src="https://media.giphy.com/media/M9gbBd9nbDrOTu1Mqx/giphy.gif"  />

###

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="30" alt="javascript logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" height="30" alt="html5 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" height="30" alt="css3 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="30" alt="python logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" height="30" alt="csharp logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/rust/rust-original.svg" height="30" alt="rust logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flutter/flutter-original.svg" height="30" alt="flutter logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dart/dart-original.svg" height="30" alt="dart logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" height="30" alt="nodejs logo"  />
</div>

###

<h2 align="left">Dinosaur Game</h2>
<canvas id="gameCanvas" width="800" height="200" style="border:1px solid #000"></canvas>
<script>
  let canvas = document.getElementById("gameCanvas");
  let ctx = canvas.getContext("2d");
  let dino = { x: 50, y: 150, width: 20, height: 20, dy: 0, gravity: 0.6, jumpPower: -10, grounded: true };
  let obstacles = [];
  let gameSpeed = 3;
  let score = 0;
  
  document.addEventListener("keydown", function(event) {
    if (event.code === "Space" && dino.grounded) {
      dino.dy = dino.jumpPower;
      dino.grounded = false;
    }
  });
  
  function update() {
    dino.dy += dino.gravity;
    dino.y += dino.dy;
    if (dino.y >= 150) {
      dino.y = 150;
      dino.dy = 0;
      dino.grounded = true;
    }
    
    if (Math.random() < 0.02) {
      obstacles.push({ x: 800, y: 160, width: 20, height: 20 });
    }
    
    for (let i = 0; i < obstacles.length; i++) {
      obstacles[i].x -= gameSpeed;
      if (obstacles[i].x + obstacles[i].width < 0) {
        obstacles.splice(i, 1);
        score++;
      }
      if (
        dino.x < obstacles[i].x + obstacles[i].width &&
        dino.x + dino.width > obstacles[i].x &&
        dino.y < obstacles[i].y + obstacles[i].height &&
        dino.y + dino.height > obstacles[i].y
      ) {
        alert("Game Over! Score: " + score);
        document.location.reload();
      }
    }
    
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = "black";
    ctx.fillRect(dino.x, dino.y, dino.width, dino.height);
    ctx.fillStyle = "red";
    for (let obs of obstacles) {
      ctx.fillRect(obs.x, obs.y, obs.width, obs.height);
    }
    requestAnimationFrame(update);
  }
  update();
</script>
