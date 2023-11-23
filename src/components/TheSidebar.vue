<script lang="ts" setup>
import { inject } from 'vue'
import type { ChessboardState } from '@/types/common'
import { defaultChessboardState } from '@/utils/defaultStates'

const chessboardState = inject<ChessboardState>('chessboardState', defaultChessboardState)
</script>

<template>
  <div class="sidebar">
    <ol class="clicked-squares">
      <li
        class="clicked-squares-record"
        v-for="(square, index) in chessboardState.clickedSquares"
        :key="index"
      >
        {{ square }}
      </li>
    </ol>
  </div>
</template>

<style scoped>
.sidebar {
  background-color: var(--color-background-mute);
  color: var(--color-text);
  padding: 20px;
  height: 100%;
  overflow: auto;
  border-radius: 5px;
}

.clicked-squares {
  list-style: none;
  padding: 0;
  counter-reset: square-counter;
}

.clicked-squares-record {
  counter-increment: square-counter;
  margin-right: 10px;
}

.clicked-squares-record::before {
  content: counter(square-counter) '. ';
}

@media (max-width: 768px) {
  .sidebar {
    height: 16vh;
    display: flex;
    align-items: center;
    min-height: 70px;
    overflow-y: scroll;
    padding: 15px;
  }

  .clicked-squares {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 10px;
  }
}
</style>
