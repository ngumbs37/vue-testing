<template>
    <div class="container">
        <div id="app" class="box row">
            <character></character>
            <div class=" four columns my-2">
                <stats :character="user.characters[2]"></stats>
                <equips></equips>
            </div>
            <characterList :list="user.characters" ></characterList>
        </div>
    </div>
</template>

<script>

    import characterList from './components/character-list.vue';
    import character from './components/character.vue';
    import stats from './components/stats.vue';
    import equips from './components/equips.vue';


    export default {
        name: 'app',
        components: {
            stats,
            characterList,
            character,
            equips
        },
        data() {
            return {
                title: 'Home',
                user: {
                    "userId": "2876349875623",
                    "username": "calvin",
                    "characters": [
                        {
                            "id": "7846",
                            "name": {
                                first: 'Reimu',
                                last: 'Hakurei',
                                other: '',
                                nick: 'miko'
                            },
                            "lv": {
                                "current": "3",
                                "max": "50"
                            },
                            "stats": {
                                "hp": "20",
                                "stamina": {
                                    "current": "12",
                                    "max": () => "15"
                                },
                                "atk": "56",
                                "def": "0",
                                "crit": "3",
                                "critDmg": "20",
                                "acc": "7",
                                "dodge": "3"
                            },
                            "Spellcards": [null, null],
                            "Weapon": "4"
                        },
                        {
                            "id": "47836",
                            "name": {
                                first: 'Marisa',
                                last: 'Kirisame',
                                other: '',
                                nick: 'marichan'
                            },
                            "lv": {
                                "current": "3",
                                "max": "50"
                            },
                            "stats": {
                                "hp": "20",
                                "stamina": {
                                    "current": "12",
                                    "max": () => "15"
                                },
                                "atk": "56",
                                "def": "0",
                                "crit": "3",
                                "critDmg": "20",
                                "acc": "7",
                                "dodge": "3"
                            },
                            "Spellcards": ["2", "5"],
                            "Weapon": "8"
                        }
                    ],
                    "Inventory": {
                        "Items": [
                            {
                                "id": "1",
                                "name": "potion",
                                "amount": "4"
                            }
                        ],
                        "Spellcards": [
                            {
                                "id": "2",
                                "ownerId": "2",
                                "name": "Love-Sign: Master-Spark",
                                "amount": "1"
                            },
                            {
                                "id": "5",
                                "ownerId": "2",
                                "name": "Love-Sign: Non-Directional-Laser",
                                "amount": "1"
                            }
                        ],
                        "Weapons": [
                            {
                                "id": "4",
                                "name": "Miko Amulet",
                                "w-stats": {
                                    "hp": "20",
                                    "atk": "56",
                                    "def": "0",
                                    "crit": "3",
                                    "critDmg": "20",
                                    "acc": "7",
                                    "dodge": "3"
                                }
                            },
                            {
                                "id": "8",
                                "name": "Mini-Hakkero",
                                "w-stats": {
                                    "hp": "0",
                                    "atk": "34",
                                    "def": "0",
                                    "crit": "3",
                                    "critDmg": "20",
                                    "acc": "6",
                                    "dodge": "5"
                                }
                            }

                        ]
                    },
                    "Money": ["534", '526', "23"]
                }
            };
        }
    }

</script>


<style src="./assets/css/skeleton.css"></style>
<style src="./assets/css/style.css"></style>