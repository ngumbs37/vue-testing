<template>
    <div class="box equips">
        <h6 class="h5">Equips</h6>
        <div class="box">
            <div class="row equips-row">
                <div class="offset-by-two three columns">
                    <div class="box eq-box" v-on:click="changeEquipMenu('head')">
                        {{ display('head') }}
                    </div>
                    <div class="box eq-box" v-on:click="changeEquipMenu('body')">
                        {{ display('body') }}
                    </div>
                </div>
                <div class="three columns">
                    <div class="box eq-box" v-on:click="changeEquipMenu('arms')">
                        {{ display('arms') }}
                    </div>
                    <div class="box eq-box" v-on:click="changeEquipMenu('legs')">
                        {{ display('legs') }}
                    </div>
                </div>
                <div class="three columns">
                    <div class="box eq-box" v-on:click="changeEquipMenu('weapon')">
                        {{ display('weapon') }}
                    </div>
                    <div class="box eq-box" v-on:click="changeEquipMenu('spellcard0')">
                        {{ display('spellcard0') }}
                    </div>
                    <div class="box eq-box" v-on:click="changeEquipMenu('spellcard1')">
                        {{ display('spellcard1') }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "equip-item",
        props: {
            "equips": {
                type: Object,
                required: true
            }
        },
        data () {
            return {
                gear: {
                    head: "0",
                    body: "1",
                    legs: "2",
                    arms: "3"
                }
            }
        },
        methods: {
            display(equipName) {
                switch(equipName){
                    case 'spellcard0':
                        return this.itemOrNone(this.equips.spellcards[0]);

                    case 'spellcard1':
                        return this.itemOrNone(this.equips.spellcards[1]);

                    default :
                        return this.itemOrNone(this.equips[equipName]);
                }
            },
            itemOrNone(item){
                if(!item.id) 
                    return "None";
                return item;
            },
            changeEquipMenu(type) {
                switch(type){
                    case 'spellcard0':
                    case 'spellcard1':
                        this.$emit('equip-menu', ['card']);
                        break
                    case 'weapon':
                        this.$emit('equip-menu',[type]);
                        break;
                    default:
                        this.$emit('equip-menu', [type, this.gear[type]]);
                }
            }
        }
    }
</script>

<style scoped>

</style>