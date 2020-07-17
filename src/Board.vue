<template>
    <div>
        <hr>
        <Tile v-for="tile of $store.state.board.tiles" :tile="tile"/>
    </div>
</template>

<script>
    import Tile from "./Tile";
    export default {
        name: "Board",
        components: {Tile}
    }
</script>

<style scoped>

</style>