<script lang="ts" setup>
// const lastClickedSquare = ref(null)

import { inject } from 'vue'
import type { ChessboardState } from '@/types/common'
import { defaultChessboardState } from '@/utils/defaultStates'

const chessboardState = inject<ChessboardState>('chessboardState', defaultChessboardState)

function handleClick(coordinates: string) {
  // lastClickedSquare.value = square
  console.log(coordinates)
  chessboardState.clickedSquares.push(coordinates)
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
  <div class="chessboard-container">
    <div class="vertical-label-container">
      <div v-for="n in 8" :key="'v' + n" class="label vertical-label">{{ 9 - n }}</div>
    </div>

    <div class="chessboard">
      <div
        v-for="index in 64"
        :key="index"
        :class="getSquareColor(index)"
        class="chess-square"
        @click="handleClick(getCoordinates(index))"
      ></div>
    </div>
    <div class="horizontal-label-container">
      <div
        v-for="letter in ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']"
        :key="letter"
        class="label horizontal-label"
      >
        {{ letter }}
      </div>
    </div>
  </div>
</template>

<style scoped>
.chessboard-container {
  display: grid;
  grid-template-columns: 30px 1fr;
  grid-template-rows: 1fr 30px;
  max-width: calc(100% - 60px);
  max-height: calc(90vh - 60px);
  justify-content: center;
  align-items: center;
}

.chessboard {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  grid-template-rows: repeat(8, 1fr);

  aspect-ratio: 1;
}

.chess-square {
  width: 100%;
  height: 100%;
  border: 1px solid #333;
}

.white-square {
  background-color: var(--chess-com-white-square);
}

.black-square {
  background-color: var(--chess-com-black-square);
}

.vertical-label-container,
.horizontal-label-container {
  height: 100%;
  display: grid;
}

.vertical-label-container {
  grid-template-rows: repeat(8, 1fr);
}

.horizontal-label-container {
  grid-template-columns: repeat(8, 1fr);
  width: 100%;
  grid-column: 2;
}

.label {
  display: flex;
  justify-content: center;
  align-items: center;
  color: var(--color-text);
}
</style>
