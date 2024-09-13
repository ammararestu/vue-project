<template>
  <div>
    <!-- Click Counter -->
    <section>
      <h2>Click Counter</h2>
      <button @click="incrementCount">Click me!</button>
      <p>Click count: {{ clickCount }}</p>
    </section>

    <!-- Box Color Changer -->
    <section>
      <h2>Box Color Changer</h2>
      <button @click="changeColor">Change Box Color</button>
      <div :style="{ backgroundColor: boxColor, width: '200px', height: '200px', margin: '20px auto' }"></div>
    </section>

    <!-- Image Carousel -->
    <section>
      <h2>Image Carousel</h2>
    <button @click="prevImage">Previous</button>
    <img :src="images[currentImage]" alt="Image Carousel" class="carousel-image"/>
    <button @click="nextImage">Next</button>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import pic1 from '@/assets/pic1.jpg'
import pic2 from '@/assets/pic2.jpg'
import pic3 from '@/assets/pic3.jpg'

// Click Counter
const clickCount = ref(0)
const incrementCount = () => {
  clickCount.value++
}

// Box Color Changer
const boxColor = ref('lightblue')
const colors = ['lightblue', 'lightgreen', 'lightcoral', 'lightgoldenrodyellow']
const changeColor = () => {
  const randomIndex = Math.floor(Math.random() * colors.length)
  boxColor.value = colors[randomIndex]
}

// Image Carousel
const images = [pic1, pic2, pic3]
const currentImage = ref(0)
const prevImage = () => {
  currentImage.value = (currentImage.value - 1 + images.length) % images.length
}
const nextImage = () => {
  currentImage.value = (currentImage.value + 1) % images.length
}
</script>

<style scoped>
/* General Styles */
button {
  font-size: 20px;
  padding: 10px 20px;
  margin: 10px;
}

section {
  margin-bottom: 40px;
  text-align: center;
}

.carousel-image {
  width: 300px;
  height: 200px;
  display: block;
  margin: 10px auto;
}
</style>