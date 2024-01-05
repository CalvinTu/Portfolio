<template>
    <div>
      <h2>Snake Game</h2>
      <div class="game-container">
        <canvas ref="gameCanvas" width="1300" height="600" class="game-canvas" @keydown="handleKeyDown" @click="focusCanvas" tabindex="0"></canvas>
        <p class="instructions">Click before you play and Use arrow keys to move</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        canvas: null,
        ctx: null,
        snake: [{ x: 10, y: 10 }],
        direction: "right",
        gridSize: 20,
        food: { x: 5, y: 5 },
      };
    },
    mounted() {
      this.canvas = this.$refs.gameCanvas;
      this.ctx = this.canvas.getContext("2d");
      this.startGame();
    },
    methods: {
      startGame() {
        setInterval(() => {
          this.moveSnake();
          this.drawGame();
        }, 100);
      },
      moveSnake() {
        const head = { ...this.snake[0] };
  
        switch (this.direction) {
          case 'up':
            head.y -= 1;
            break;
          case 'down':
            head.y += 1;
            break;
          case 'left':
            head.x -= 1;
            break;
          case 'right':
            head.x += 1;
            break;
        }
  
        if (this.checkCollision(head)) {
          console.log('Game Over!');
          return;
        }
  
        if (this.hasEatenFood(head)) {
          this.snake.unshift(head);
          this.generateNewFood();
        } else {
          this.snake.unshift(head);
          this.snake.pop();
        }
      },
      checkCollision(head) {
        return (
          head.x < 0 ||
          head.x * this.gridSize >= this.canvas.width ||
          head.y < 0 ||
          head.y * this.gridSize >= this.canvas.height ||
          this.snake.some(segment => segment.x === head.x && segment.y === head.y)
        );
      },
      hasEatenFood(head) {
        return head.x === this.food.x && head.y === this.food.y;
      },
      generateNewFood() {
        this.food = {
          x: Math.floor(Math.random() * (this.canvas.width / this.gridSize)),
          y: Math.floor(Math.random() * (this.canvas.height / this.gridSize)),
        };
      },
      drawGame() {
        this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);
        this.drawSnake();
        this.drawFood();
      },
      drawSnake() {
        this.ctx.fillStyle = "green";
        this.snake.forEach(segment => {
          this.ctx.fillRect(
            segment.x * this.gridSize,
            segment.y * this.gridSize,
            this.gridSize,
            this.gridSize
          );
        });
      },
      drawFood() {
        this.ctx.fillStyle = "red";
        this.ctx.fillRect(
          this.food.x * this.gridSize,
          this.food.y * this.gridSize,
          this.gridSize,
          this.gridSize
        );
      },
      handleKeyDown(event) {
        switch (event.key) {
          case 'ArrowUp':
            this.direction = 'up';
            break;
          case 'ArrowDown':
            this.direction = 'down';
            break;
          case 'ArrowLeft':
            this.direction = 'left';
            break;
          case 'ArrowRight':
            this.direction = 'right';
            break;
        }
      },
      focusCanvas() {
        // Focus on the canvas to capture keyboard events
        this.canvas.focus();
      },
    },
  };
  </script>
  
  <style scoped>
  /* Add your game styling here */
  .game-container {
    position: relative;
  }
  
  .game-canvas {
    border: 2px solid #000; /* Border styling */
    cursor: pointer;
  }
  
  .instructions {
    text-align: center;
    font-size: 16px;
  }
  </style>
  