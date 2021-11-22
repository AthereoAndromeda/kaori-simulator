<script setup lang="ts">
import KS from "./components/KaoriSimulator.vue";
</script>

<template>
  <KS />

  <footer>
    <p>
      Fork me on
      <a href="https://github.com/AthereoAndromeda/kaori-simulator">GitHub</a>
    </p>
    <p>
      Powered by <a href="https://icanhazdadjoke.com">icanhazdadjoke API</a>
    </p>
  </footer>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

footer {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
