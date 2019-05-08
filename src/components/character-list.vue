<template>
    <div class="box four columns h-25 my-2">
        <div class="box ten columns" v-for="item in list" :key="item.id">
            <name :name="item.name" @update="$emit('update', item.id)"></name>
        </div>
    </div>
</template>

<script>
    import name from './name.vue';

    export default {
        components: {
            name
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