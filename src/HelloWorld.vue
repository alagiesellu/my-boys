<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      That's my boys!
    </p>
    <h3>Start Game</h3>
    <ul>
      <li>
        <button @click="makeTiles('boys.jpeg')">Salam</button>
      </li>
      <li>
        <button @click="makeTiles('boys.jpeg')">Alieu</button>
      </li>
      <li>
        <button @click="makeTiles('boys.jpeg')">Bala</button>
      </li>
    </ul>
    <br>
    <input type="file" @change="onFileChange" accept="image/*">
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    onFileChange(e) {
      this.makeTiles( URL.createObjectURL(e.target.files[0]));
    },
    makeTiles(tile) {

      let tiles = [];
      let shuffled = this.shuffle(['*',1,2,3,4,5,6,7,8]);

      let i = 0, j = 0;
      while (j < 3)
      {
        tiles[j] = [];
        while (i < 3)
        {
          tiles[j][i] = shuffled.pop();
          i += 1;
        }
        i = 0;
        j += 1;
      }

      this.$store.state.board = {
        img: tile,
        tiles: tiles
      };
    },
    shuffle(arra1) {
      var ctr = arra1.length, temp, index;

    // While there are elements in the array
      while (ctr > 0) {
    // Pick a random index
        index = Math.floor(Math.random() * ctr);
    // Decrease ctr by 1
        ctr--;
    // And swap the last element with it
        temp = arra1[ctr];
        arra1[ctr] = arra1[index];
        arra1[index] = temp;
      }
      return arra1;
    }
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
