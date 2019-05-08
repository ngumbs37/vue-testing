<template>
    <div class="box four columns h-25 my-2">
        <h6 class="h5">Character Sprite</h6>
        <div class="box h-100">
            <img id="img" v-bind:src="image()" alt="">
        </div>
    </div>
</template>

<script>

    export default {
        name: "character",
        methods: {
            image: () => "./logo.png"
        }
    }
</script>

<style scoped>

</style>