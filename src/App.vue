<script setup lang="ts">
import TheChessboard from '@/components/TheChessboard.vue'
import TheSidebar from '@/components/TheSidebar.vue'
import { provide, reactive } from 'vue'
import type { ChessboardState } from '@/types/common'

const chessboardState: ChessboardState = reactive({
  clickedSquares: []
})

provide('chessboardState', chessboardState)
</script>

<template>
  <main>
    <div class="app-container">
      <TheChessboard />
      <TheSidebar />
    </div>
  </main>
</template>

<style scoped>
.app-container {
  display: grid;
  grid-template-columns: 70% auto;
  gap: 32px;
  align-items: center;
}

@media (max-width: 768px) {
  .app-container {
    grid-template-columns: auto;
    min-height: 92vh;
    align-content: start;
  }
}
</style>
