<template>
    <div class="box equips">
        <h6 class="h5">Equips</h6>
        <div class="box">
            <div class="row equips-row">
                <div class="offset-by-two three columns">
                    <div class="box eq-box">
                        {{ display('head') }}
                    </div>
                    <div class="box eq-box">
                        {{ display('body') }}
                    </div>

                </div>
                <div class="three columns">
                    <div class="box eq-box">
                        {{ display('arms') }}
                    </div>
                    <div class="box eq-box">
                        {{ display('legs') }}
                    </div>
                </div>
                <div class="three columns">
                    <div class="box eq-box">
                        {{ display('weapon') }}
                    </div>
                    <div class="box eq-box">
                        {{ display('spellcard0') }}
                    </div>
                    <div class="box eq-box">
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
            }
        }
    }
</script>

<style scoped>

</style>