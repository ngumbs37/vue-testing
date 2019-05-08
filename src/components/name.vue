<template>
    <div >
        <span v-if="name.other !== ''"
              class="one-half column">{{ name.last + ' ' + name.other + ' ' + name.first }}
            <span v-if="name.nick !== ''"> ({{ name.nick }})</span></span>
        <span v-else class="one-half column">{{ name.last + ' ' + name.first }}
            <span v-if="name.nick !== ''"> ({{ name.nick }})</span></span>
    </div>
</template>

<script>
    export default {
        name: "name",
        props: ["name","index"]
    }
</script>

<style scoped>

</style>