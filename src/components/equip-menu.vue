<template>
<div id="side-menu">
    <div class="container">
      <div class="row">
        <div class="box four column" v-for="gear in equippable(inventory, eqType, character)" :key="gear.id">
        {{ gear.name }} <br> {{ gear.type }} </div>
      </div>
    </div>
</div>
</template>

<script>
    export default {
        name: "equip-menu",
        props: {
            inventory: {
                type: Array,
                required: true
            },
            character: {
                type: Object,
                required: true
            },
            eqType: {
                type: String,
                required: true,
                default: "0",
                validator(input) {
                    return Number.isInteger(parseInt(input))
                }
            }
        },
        methods: {
            equippable: (gear, type, owner) => {
                let arr = [];
                if(gear.length < 1 )
                return [];
                
                if(gear[0]["e-stats"] != undefined) {
                    for(let i = 0; i < gear.length; i++) {
                        if(gear[i].type[0] === type || gear[i].type[1] === type) {
                            // console.log(JSON.stringify(gear[i]))
                            if (gear[i].ownerId == "none" || gear[i].ownerId == owner.id) {
                                arr.push(gear[i])
                            }
                        }
                    }
                } else {
                    for(let i = 0; i < gear.length; i++) {
                        if (gear[i].ownerId == "none" || gear[i].ownerId == owner.id) {
                            console.log(gear[i])
                            if(gear[i].class == null)
                                arr.push(gear[i])
                            else {
                                if(gear[i].class == "none" || gear[i].class == owner.class)
                                arr.push(gear[i])
                            }
                        }
                    }
                }

                if(arr.length < 1 )
                return [{name: 'Nothing to equip'}];

                return arr.sort((a, b) => a.name !== b.name ? a.name < b.name ? -1 : 1 : 0);
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
#side-menu{
    z-index: 1000;
    float: right;
    margin-left: auto;
    margin-right: 0;
    height: 100%;
    width: 25%;
}
</style>