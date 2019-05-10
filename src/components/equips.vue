<template>
    <div class="box equips">
        <h6 class="h5">Equips</h6>
        <div class="box">
            <div class="row equips-row">
                <div class="offset-by-two three columns">
                    <div class="box eq-box">
                        {{ equips.Head }}
                    </div>
                    <div class="box eq-box">
                        {{ equips.Body }}
                    </div>

                </div>
                <div class="three columns">

                    <div class="box eq-box">
                        {{ equips.Arms }}
                    </div>
                    <div class="box eq-box">
                        {{ equips.Legs }}
                    </div>
                </div>
                <div class="three columns">
                    <div class="box eq-box">
                        {{ equips.Weapon }}
                    </div>
                    <div class="box eq-box">
                        {{ equips.Spellcards[0] }}
                    </div>
                    <div class="box eq-box">
                        {{ equips.Spellcards[1] }}
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
        }
    }
</script>

<style scoped>

</style>