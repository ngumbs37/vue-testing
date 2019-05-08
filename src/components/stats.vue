<template>

        <div class="box mb-2">
            <h6 class="h5">Stats</h6>
            <div class="box stats">
                <div class="row">
                    <name :name="character.name"></name>
                    <p class="one-half column">Lv {{character.lv.current}} / {{character.lv.max}}</p>
                </div>
                <div class="row">
                    <p class="one-half column">Hp: {{character.stats.hp}}</p>
                    <p class="one-half column">Stam:
                        {{character.stats.stamina.current}}/{{character.stats.stamina.max()}} <span>(00:00)</span></p>
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
    import name from './name.vue';
  export default {
      components: {
          name
      },
    props: {
      character : {
          type: Object,
          required: true,
        stats: {
          type: Object,
          required: true,
          validator(stat) {
            return Number.isInteger(stat.hp)
                && Number.isInteger(stat.atk)
                && Number.isInteger(stat.def)
                && Number.isInteger(stat.crit)
                && Number.isInteger(stat.critDmg)
                && Number.isInteger(stat.acc)
                && Number.isInteger(stat.dodge)
                && (typeof stat.stamina.current === 'number') && (typeof stat.stamina.max === 'function')
                && stat.stamina.current <= 15 && stat.stamina.max() === 15 && Number.isInteger(stat.stamina.current);
          }
        }
      }
    }
  }
</script>

<style scoped>

</style>
