<template>
    <div class="box four columns h-25 my-2">
        <h6 class="h5">Character List</h6>
        <div class="box h-100">
            <div class="box ten columns offset-by-one mt-1" v-for="character in list" :key="character.id">
                <characterName :name="character.name" @click="$emit('update', item.id)"></characterName>
            </div>
        </div>
    </div>
</template>

<script>
    import characterName from './name.vue';

    export default {
        components: {
            characterName
        },
        props: {
            list: {
                type: Array,
                required: true
            }
        },
        name: "character-list"
    }
</script>

<style scoped>

</style>