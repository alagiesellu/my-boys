<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      That's my boys!
    </p>
    <h3>Start Game</h3>
    <ul>
      <li>
        <button @click="start('boys.jpeg')">Salam</button>
      </li>
      <li>
        <button @click="start('boys.jpeg')">Alieu</button>
      </li>
      <li>
        <button @click="start('boys.jpeg')">Bala</button>
      </li>
    </ul>
    <br>
    <input type="file" @change="onFileChange">
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    start(img) {
      this.makeTiles('/'+img);
    },
    onFileChange(e) {
      this.makeTiles( URL.createObjectURL(e.target.files[0]));
    },
    makeTiles(tile) {
      this.$store.state.board = {
        img: tile,
        tiles: new Array(9)
      };
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a, button, input {
  color: #42b983;
}
button {
  border: solid;
  font-size: 20px;
}
</style>
