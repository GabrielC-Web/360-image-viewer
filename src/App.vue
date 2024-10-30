
<script setup>

  import { onMounted } from 'vue';
import img from './assets/01-8192.jpg'

  let canvas
  let ctx
  let image = new Image()
  let offsetX = 0; 
  image.src = img
  let imgWidth = image.width / 5
  let isDragging = false;

  onMounted(() => {
    canvas = document.getElementById('viewer')

    createCanvas()

  })

  function createCanvas() {
    ctx = canvas?.getContext('2d');

    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
  

    image.onload = () => {

      draw()

    }
  }

  function draw() {

    ctx?.drawImage(image, offsetX, 0, imgWidth, image.height, 0, 0, canvas.width, canvas.height);
    
  }

  function handleMouseDown(params) {
    offsetX+=imgWidth/10
    draw()
  }

</script>

<template>

  <div class="bg-slate-200 h-svh w-svw flex justify-center items-center">
    <canvas id="viewer" v-on:mousedown="handleMouseDown($event)"></canvas>
  </div>

</template>

<style scoped>

</style>
