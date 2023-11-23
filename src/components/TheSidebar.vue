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
  overflow-y: auto;
  border-radius: 5px;
  max-height: 90vh;
}

.clicked-squares {
  list-style: none;
  padding: 0;
  counter-reset: square-counter;
  column-count: 3;
}

.clicked-squares-record {
  counter-increment: square-counter;
}

.clicked-squares-record::before {
  content: counter(square-counter) '. ';
}

@media (max-width: 992px) {
  .clicked-squares {
    column-count: 2;
    column-gap: 20px;
  }
}

@media (max-width: 768px) {
  .sidebar {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    min-height: 70px;
    overflow: auto;
    padding: 15px;
    max-height: 20vh;
  }

  .clicked-squares {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 10px;
    column-count: 1;
  }
}
</style>
