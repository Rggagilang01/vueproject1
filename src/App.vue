<template>
  <div id="app">
    <div class="title-container">
      <h1 class="main-title">Apps Vue By'Rangga</h1>
    </div>
    <div class="card-wrapper">
      <div class="card" id="click-counter-card">
        <h2>Click Counter</h2>
        <p class="count">{{ count }} Clicks</p>
        <div class="button-group bottom-buttons">
          <button class="btn" @click="decrementCount">-</button>
          <button class="btn" @click="incrementCount">+</button>
          <button class="btn reset-btn" @click="resetCount">Reset</button>
        </div>
      </div>
      <div class="card" id="color-changer-card">
        <h2>Box Color Changer</h2>
        <div :style="{ backgroundColor: color }" class="color-box"></div>
        <div class="color-options">
          <div v-for="option in colors" :key="option" :style="{ backgroundColor: option }" class="color-option" @click="setColor(option)"></div>
        </div>
        <button class="btn change-color-btn" @click="randomizeColor">Change Color</button>
      </div>
    </div>
    <div class="card" id="carousel-card">
      <h2>Image Carousel</h2>
      <div class="carousel">
        <img :src="images[currentImage]" alt="Image Carousel" />
      </div>
      <div class="carousel-controls">
        <button class="btn" @click="prevImage">&#8249;</button> <!-- Panah kiri -->
        <button class="btn" @click="nextImage">&#8250;</button> <!-- Panah kanan -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      color: '#f39c12',
      colors: ['#e74c3c', '#f39c12', '#f1c40f', '#2ecc71', '#3498db', '#9b59b6'],
      currentImage: 0,
      images: [
        'https://i.pinimg.com/564x/b9/76/22/b97622a94ccc52ca428e6a2b4173d388.jpg',
        'https://i.pinimg.com/originals/4f/ef/18/4fef186ddd03c91499bdeec5856840df.jpg',
        'https://i.pinimg.com/564x/dd/fb/8c/ddfb8c295ffecee0ac7f90a34106fada.jpg'
      ]
    };
  },
  methods: {
    incrementCount() {
      this.count++;
    },
    decrementCount() {
      if (this.count > 0) this.count--;
    },
    resetCount() {  
      this.count = 0;
    },
    setColor(color) {
      this.color = color;
    },
    randomizeColor() {
      const randomColor = this.colors[Math.floor(Math.random() * this.colors.length)];
      this.color = randomColor;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage =
        (this.currentImage - 1 + this.images.length) % this.images.length;
    }
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Happy+Hell:wght@700&family=Baltica:wght@400&family=Montserrat:wght@400&display=swap');

#app {
  background: linear-gradient(45deg, #ff6b6b, #f39c12);
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  overflow: hidden;
}

.title-container {
  animation: fadeIn 2s ease-out;
}

.main-title {
  font-family: 'Happy Hell', cursive;
  font-size: 50px;
  color: #fff;
  text-align: center;
  margin-bottom: 30px;
}

.card-wrapper {
  display: flex;
  justify-content: space-between;
  width: 100%;
  max-width: 680px;
  margin-bottom: 20px;
  animation: slideIn 2s ease-out;
}

.card {
  border-radius: 20px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
  background-color: #fff;
  margin: 20px;
  padding: 20px;
  text-align: center;
  transition: transform 0.3s ease-in-out;
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

#click-counter-card {
  animation: dropIn 1.5s ease-out;
}

#color-changer-card {
  animation: dropIn 1.5s ease-out;
}

#carousel-card {
  width: 100%;
  max-width: 600px;
  animation: riseIn 1.5s ease-out;
}

h2 {
  font-family: 'Baltica', sans-serif;
  font-size: 24px;
  margin-bottom: 15px;
}

.count {
  font-family: 'Montserrat', sans-serif;
  font-size: 30px;
  margin-bottom: 20px;
  color: #333;
}

.btn {
  background-color: #f39c12;
  border: none;
  padding: 10px 20px;
  font-size: 18px;
  color: #fff;
  border-radius: 5px;
  cursor: pointer;
  margin: 5px;
  transition: background 0.3s ease;
}

.btn:hover {
  background-color: #e67e22;
}

.reset-btn {
  background-color: #e74c3c;
}

.reset-btn:hover {
  background-color: #c0392b;
}

.change-color-btn {
  margin-top: 20px;
}

.color-box {
  width: 100px;
  height: 100px;
  border-radius: 10px;
  margin: 20px auto;
  transition: background-color 0.3s ease;
}

.color-options {
  display: flex;
  justify-content: center;
  gap: 10px;
}

.color-option {
  width: 30px;
  height: 30px;
  border-radius: 5px;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.color-option:hover {
  transform: scale(1.2);
}

.carousel {
  width: 100%;
  overflow: hidden;
  margin-bottom: 20px;
}

.carousel img {
  width: 100%;
  height: auto;
  border-radius: 10px;
}

.carousel-controls {
  display: flex;
  justify-content: space-between;
}

.carousel-controls .btn {
  padding: 10px;
  font-size: 24px; /* Sesuaikan ukuran font untuk ikon panah */
}

@keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
}

@keyframes slideIn {
  0% { transform: translateY(-50px); opacity: 0; }
  100% { transform: translateY(0); opacity: 1; }
}

@keyframes dropIn {
  0% { transform: translateY(-200px); opacity: 0; }
  100% { transform: translateY(0); opacity: 1; }
}

@keyframes riseIn {
  0% { transform: translateY(200px); opacity: 0; }
  100% { transform: translateY(0); opacity: 1; }
}
</style>
