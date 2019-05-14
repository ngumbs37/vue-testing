<template>
    <div class="box mb-2">
        <h6 class="h5">Stats</h6>
        <div class="box stats">
            <div class="row">
                <characterName :name="character.name"></characterName>
                <p class="one-half column">Lv {{ getLv() }}</p>
            </div>
            <div class="row">
                <p class="one-half column">Hp: {{ getStat('hp') }}</p>
                <p class="one-half column">Stam: {{ getStam() }} <span>(00:00)</span></p>
            </div>
            <div class="row">
                <p class="one-half column">Atk: {{ getStat('atk') }}</p>
                <p class="one-half column">Def: {{ getStat('def') }}</p>
            </div>
            <div class="row">
                <p class="one-half column">Crit: {{ getStat('crit') }}</p>
                <p class="one-half column">Crit Dmg: {{ getStat('critDmg') }}</p>
            </div>
            <div class="row">
                <p class="one-half column">Acc: {{ getStat('acc') }}</p>
                <p class="one-half column">Dodge: {{ getStat('dodge') }}</p>
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
            character: {
                type: Object,
                required: true,
                validator(input) {
                    return Number.isInteger(parseInt(input.stats.hp))
                      && Number.isInteger(parseInt(input.stats.atk))
                      && Number.isInteger(parseInt(input.stats.def))
                      && Number.isInteger(parseInt(input.stats.crit))
                      && Number.isInteger(parseInt(input.stats.critDmg))
                      && Number.isInteger(parseInt(input.stats.acc))
                      && Number.isInteger(parseInt(input.stats.dodge))
                      && Number.isInteger(parseInt(input.stats.stamina.current))
                      && Number.isInteger(parseInt(input.stats.stamina.max))
                      && parseInt(input.stats.stamina.current) <= 15 
                      && parseInt(input.stats.stamina.max) === 15;
                }
            }
        },
        methods: {
            getStat(stat){
                return this.character.stats[stat];
            },
            getLv(){
                return `${this.character.lv.current} / ${this.character.lv.max}`
            },
            getStam(){
                return `${this.character.stats.stamina.current} / ${this.character.stats.stamina.max}`
            }
        }
    }
</script>

<style scoped>

</style>
