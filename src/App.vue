<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div>
  <header><h1>Jonathon Fick Garden Consulting</h1></header>
  
    <div class="canvasDiv">
       <Suspense>
    <HelloWorld msg="Vite + Vue" />
    </Suspense>
    </div>
   <div class="navDiv">
      <div onclick="handleClick(0)">
        Intro
      </div>
      <div onclick="handleClick(1)">
        Work
      </div>
      <div onclick="handleClick(2)">
        Simulations
      </div>
      <div onclick="handleClick(3)">
        About
      </div>
      <div onclick="handleClick(4)">
        Contact
      </div>

    </div>
  </div>
  
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
