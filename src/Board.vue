<template>
    <div style="width:40%;display:table;margin:auto;">
        <hr>
        <h1 class="active" v-if="has_won">Winner!!!</h1>
        <div class="grid-container" v-bind:style="{ backgroundImage: 'url('+$store.state.board.img+')' }">
            <div v-for="(row, x) in $store.state.board.tiles">
                <div v-for="(tile, y) in row" class="grid-item" @click="move(x, y)">
                    {{tile}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Board",
        data() {
            return {
                empty_x_y: [],
                final_board: [1,2,3,4,5,6,7,8,'*'],
                has_won: false,
            }
        },
        created() {
            for (let x in this.$store.state.board.tiles)
                for (let y in this.$store.state.board.tiles[x])
                    if (this.$store.state.board.tiles[x][y] === '*')
                        this.empty_x_y = [x*1, y*1];
        },
        methods: {
            movable(tile_x, tile_y) {

                let diff = 0;

                if (this.empty_x_y[0] === tile_x)
                    diff = this.empty_x_y[1] - tile_y;

                else if (this.empty_x_y[1] === tile_y)
                    diff = this.empty_x_y[0] - tile_x;

                return diff === 1 || diff === -1;
            },
            winner() {
                let counter = 0;
                for (let x in this.$store.state.board.tiles)
                    for (let y in this.$store.state.board.tiles[x])
                    {
                        if (this.$store.state.board.tiles[x][y] !== this.final_board[counter])
                            return false;
                        counter += 1;
                    }
                return true;
            },
            move(tile_x, tile_y) {

                if (this.movable(tile_x, tile_y))
                {
                    this.$store.state.board.tiles[this.empty_x_y[0]][this.empty_x_y[1]] = this.$store.state.board.tiles[tile_x][tile_y];
                    this.$store.state.board.tiles[tile_x][tile_y] = '*';
                    this.empty_x_y = [tile_x, tile_y];
                    this.has_won = this.winner();
                    this.$forceUpdate();
                }
            }
        },
    }
</script>

<style scoped>
    .grid-container {
        display: grid;
        grid-template-columns: auto auto auto;
        background-color: #2196F3;
        /*padding: 20px;*/
        background-repeat: no-repeat;
        background-attachment: fixed;
        background-position: center;
    }
    .active {
        color: green;
    }
    .grid-item {
        border: 1px solid rgba(0, 0, 0, 0.8);
        padding: 50px;
        font-size: 50px;
        font-weight: bold;
        color: black;
        text-align: center;
        background-color: white;
        opacity: 0.5;
    }
</style>