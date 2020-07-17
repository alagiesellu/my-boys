<template>
  <div id="app">
    <div v-if="$store.state.board.img">
      <button class="btn btn-danger" @click="$store.state.board = {}">End Game</button>
      <Board/>
    </div>
    <div v-else>
      <img alt="Vue logo" src="logo.png">
      <HelloWorld msg="Welcome"/>
    </div>
  </div>
</template>

<script>
import HelloWorld from './HelloWorld'
import Board from "./Board";

export default {
  name: 'App',
  components: {
    Board,
    HelloWorld
  },
  data() {
    return {
    }
  },
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
a, button {
  color: red;
}
button {
  border: solid;
  font-size: 20px;
}
</style>
