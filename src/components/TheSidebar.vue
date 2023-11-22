<script lang="ts" setup>
import { inject } from 'vue'

const chessboardState = inject('chessboardState')
</script>

<template>
  <div class="sidebar">
    <ol class="clicked-squares">
      <li v-for="(square, index) in chessboardState.clickedSquares" :key="index">
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
}
</style>
