<script setup lang="ts">
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
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
  <header>
    <!--    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />-->

    <!--    <div class="wrapper">-->
    <!--      <HelloWorld msg="You did it!" />-->
    <!--    </div>-->
  </header>

  <main>
    <!--    <TheWelcome />-->
    <div class="app-container">
      <TheChessboard />
      <TheSidebar />
    </div>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

main {
  width: 100%;
  height: 100%;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

.app-container {
  display: grid;
  grid-template-columns: 1fr 300px;
  gap: 20px;
  padding: 20px;
}

@media (max-width: 768px) {
  .app-container {
    grid-template-columns: 1fr;
    grid-template-rows: auto auto;
  }
}
</style>
