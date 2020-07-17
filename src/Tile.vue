<template>
    <img width="30%" :alt="$store.state.board.img" :src="$store.state.board.img">
</template>

<script>
    export default {
        name: "Tile",
        props: {
            tile: Object
        },
    }
</script>

<style scoped>
img {
    padding: 1px 3px;
}
</style>