<template>
    <div class="box four columns h-25 my-2">
        <img id="img" v-bind:src="image()" alt="">
    </div>
</template>

<script>

    export default {
        name: "character",
        data() {
            return {
                giveName: {
                    first: 'Reimu',
                    last: 'Hakurei',
                    other: '',
                    nick: 'miko'
                },
                otherName: {
                    first: 'Mokou',
                    last: 'Fujiwara',
                    other: 'no',
                    nick: 'pheonix'
                },
                givenStats: {
                    hp: 2.0,
                    stamina: {
                        current: 11,
                        max: () => 15
                    },
                    atk: 3456,
                    def: 235,
                    crit: 343,
                    critDmg: 2,
                    acc: 67,
                    dodge: 35
                }
            }
        },
        methods: {
            image: () => "../assets/images/logo.png"
        }
    }
</script>

<style scoped>

</style>