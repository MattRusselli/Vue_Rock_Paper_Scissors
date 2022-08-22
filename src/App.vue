<template>
  <div id="app">
    <div class="flex-row buttons"></div>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {}
}
</script>

<style>
html {
  background-color: #383838;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  color: #f4f6f9;
}

.flex-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.flex-item {
  padding: 1em;
  max-height: 12em;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  background-color: #303030;
  border-radius: 4px;
  border: 1px solid rgba(255, 255, 255, 0);
  color: #f4f6f9;
}

button {
  border: 0;
  cursor: pointer;
  transition: all 0.3s ease;
}

button:disabled {
  cursor: not-allowed;
}

button:hover:not(:disabled) {
  opacity: 0.8;
  border: 1px solid rgba(255, 255, 255, 0.4);
}

.flex-item img {
  width: 250px;
  max-height: 8em;
  align-content: center;
  object-fit: contain;
}

.winner-circle {
  margin-top: 2em;
  border: 1px solid rgba(255, 255, 255, 0.2);
  padding: 1em;
  border-radius: 4px;
}

.winner-circle button {
  padding: 1em 2em;
  border-radius: 4px;
  border: 0;
  background-color: #ffcc00;
  font-weight: 700;
}

.winner-circle button:hover {
  border: 0;
}
</style>
