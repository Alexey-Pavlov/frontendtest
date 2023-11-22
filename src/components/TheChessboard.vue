<script setup lang="ts">
import { ref } from 'vue'

// const lastClickedSquare = ref(null)

function handleClick(coordinates: string) {
  // lastClickedSquare.value = square
  console.log(coordinates)
  // Additional logic for highlighting or other functionalities
}

function getCoordinates(index: number): string {
  const letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
  const x = (index - 1) % 8
  const y = Math.floor((index - 1) / 8)
  return `${letters[x]}${8 - y}`
}

function getSquareColor(index: number) {
  const x = (index - 1) % 8
  const y = Math.floor((index - 1) / 8)
  return (x + y) % 2 === 0 ? 'white-square' : 'black-square'
}
</script>

<template>
  <div class="chessboard">
    <div
      v-for="index in 64"
      :key="index"
      class="chess-square"
      :class="getSquareColor(index)"
      @click="handleClick(getCoordinates(index))"
    ></div>
  </div>
</template>

<style scoped>
.chessboard {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  grid-template-rows: repeat(8, 1fr);
  max-width: 100%;
  aspect-ratio: 1;
  max-height: 90vh;
}

.chess-square {
  width: 100%;
  height: 100%;
  border: 1px solid #333;
}

.white-square {
  background-color: #fff;
}

.black-square {
  background-color: #000;
}
</style>
