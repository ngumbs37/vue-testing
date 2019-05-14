<template>
  <slide-menu right>
    <div class="container">
      <div class="row">
        <div class="box four columns" v-for="gear in equippable(inventory.gear, '2')" :key="gear.id">
        {{ gear.name }} <br> {{ gear.type }} </div>
      </div>
    </div>
  </slide-menu>
</template>

<script>
import { Slide } from "vue-burger-menu";
export default {
  name: "equip-menu",
  props: {
    inventory: {
      type: Object,
      required: true
    },
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
  components: {
    "slide-menu": Slide
  },
  methods:{
      equippable: (gear, type) => {
        let arr = [];
            for(let i = 0; i < gear.length; i++){
                if(gear[i].type[0] === type || (gear[i].type[1] === type))
                arr.push(gear[i])
            }
        return arr
      }
  }
};
</script>

<style scoped>
.container{
    width: 95%
}
div.columns{
    height: 10em;
    overflow: hidden;
}
</style>