<template>
    <div class="box mb-2">
        <h6 class="h5">Stats</h6>
        <div class="box stats">
            <div class="row">
                <characterName :name="character.name"></characterName>
                <p class="one-half column">Lv {{character.lv.current}} / {{character.lv.max}}</p>
            </div>
            <div class="row">
                <p class="one-half column">Hp: {{character.stats.hp}}</p>
                <p class="one-half column">Stam:
                    {{character.stats.stamina.current}} / {{character.stats.stamina.max()}} <span>(00:00)</span></p>
            </div>
            <div class="row">
                <p class="one-half column">Atk: {{character.stats.atk}}</p>
                <p class="one-half column">Def: {{character.stats.def}}</p>
            </div>
            <div class="row">
                <p class="one-half column">Crit: {{character.stats.crit}}</p>
                <p class="one-half column">Crit Dmg: {{character.stats.critDmg}}</p>
            </div>
            <div class="row">
                <p class="one-half column">Acc: {{character.stats.acc}}</p>
                <p class="one-half column">Dodge: {{character.stats.dodge}}</p>
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
                      && (typeof parseInt(input.stats.stamina.current) === 'number') && (typeof input.stats.stamina.max === 'function')
                      && parseInt(input.stats.stamina.current) <= 15 && parseInt(input.stats.stamina.max()) === 15 && Number.isInteger(parseInt(input.stats.stamina.current));
                }
            }
        }
    }
</script>

<style scoped>

</style>
