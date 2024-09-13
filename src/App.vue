<template>
  <div>
    <h1>Adesti</h1>
    <h3>Click Count: {{ counter }}</h3>
    <button @click="increaseCount">Increase</button>

    <div :style="{ backgroundColor: dynamicColor }" class="box">
      This box changes randomly.
    </div>
    <button @click="randomizeColor">Randomize Color</button>

    <div class="carousel-wrapper">
      <img :src="imageList[currentImage]" alt="Image Carousel" class="carousel-image" />
    </div>
    <div class="carousel-controls">
      <button @click="previousImage" class="control-btn">Previous</button>
      <button @click="nextImage" class="control-btn">Next</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 0,
      dynamicColor: '#3498db', // Initial color
      currentImage: 0,
      imageList: [
        'https://picsum.photos/300/200?random=10',
        'https://picsum.photos/300/200?random=20',
        'https://picsum.photos/300/200?random=30'
      ]
    };
  },
  methods: {
    increaseCount() {
      this.counter++;
    },
    randomizeColor() {
      const randomColor = `#${Math.floor(Math.random() * 16777215).toString(16)}`;
      this.dynamicColor = randomColor;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.imageList.length;
    },
    previousImage() {
      this.currentImage = (this.currentImage - 1 + this.imageList.length) % this.imageList.length;
    }
  }
};
</script>

<style>
body {
  background-color: #eaecee;
}

h1 {
  color: #2c3e50;
  font-family: 'Arial', sans-serif;
}

button {
  background-color: #2ecc71;
  color: white;
  border: none;
  border-radius: 15px;
  padding: 10px 15px;
  margin: 10px;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background-color: #27ae60;
}

.box {
  width: 200px;
  height: 150px;
  margin: 20px auto;
  transition: background-color 0.5s ease;
  border-radius: 15px;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

.carousel-wrapper {
  margin: 20px auto;
  text-align: center;
}

.carousel-image {
  width: 100%;
  max-width: 300px;
  height: auto;
  border-radius: 10px;
}

.carousel-controls {
  margin-top: 10px;
}

.control-btn {
  background-color: #e74c3c;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
}

.control-btn:hover {
  background-color: #c0392b;
}
</style>
