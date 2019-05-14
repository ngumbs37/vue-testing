<template>
    <div class="container">
        <div id="app" class="box row">
            <character></character>
            <div class="four columns my-2">
                <stats :character="giveCharacter"></stats>
                <equips :equips="giveEquips"></equips>
            </div>
            <characterList :list="user.characters" v-on:update-eq="characterChange"></characterList>
        </div>
    </div>
</template>

<script>
    import characterList from './components/character-list.vue';
    import character from './components/character.vue';
    import stats from './components/stats.vue';
    import equips from './components/equips.vue';
    import user from '../userSkeleton.json';
    // eslint-disable-next-line
    const dummyUser = {
        "userId": "2876349875623",
        "username": "calvin",
        "characters": [
            {
                "id": "7846",
                "name": {
                    "first": 'Reimu',
                    "last": 'Hakurei',
                    "other": '',
                    "nick": ''
                },
                "species": "Human",

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
                "Equips": {
                    "Spellcards": [null, null],
                    "Weapon": "4",
                    "Head": "Ribbon",
                    "Body": "Sleeveless Shirt",
                    "Legs": "Red Skirt",
                    "Arms": "Detached Sleeves"
                }
            },
            {
                "id": "47836",
                "name": {
                    "first": 'Marisa',
                    "last": 'Kirisame',
                    "other": '',
                    "nick": 'marichan'
                },
                "species": "Human",

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
                "Equips": {
                    "Spellcards": ["2", "5"],
                    "Weapon": "8",
                    "Head": "Witch Hat",
                    "Body": "Black Maid Dress with Apron",
                    "Legs": "Black Maid Dress with Apron",
                    "Arms": "None"
                }
            },
            {
                "id": "1",
                "name": {
                    "first": 'Lily',
                    "last": 'White',
                    "other": '',
                    "nick": ''
                },
                "species": "Fairy",

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
                "Equips": {
                    "Spellcards": ["2", "5"],
                    "Weapon": "8",
                    "Head": "None",
                    "Body": "None",
                    "Legs": "None",
                    "Arms": "None"
                }
            },
            {
                "id": "2",
                "lastName": null,
                "firstName": "Cirno",
                "species": "Fairy",
                "spellCards": ["Ice Sign \"Icicle Fall\"", "Hail Sign \"Hailstorm\"", "Freeze Sign \"Perfect Freeze\"", "Snow Sign \"Diamond Blizzard\"", "Frost Sign \"Frost Columns\"", "Icicle Attack", "Freeze Sign \"Cold Divinity\"", "Freeze Sign \"Minus K\"", "Ice Sign \"Icicle Machine Gun\"", "Ice Sign \"Fairy Spin\"", "Ice Cubes \"Cold Sprinkler\"", "Cold Body \"Super Ice Kick\"", "Ice Sign \"Sword Freezer\"", "Frozen Sign \"Freeze Atmosphere\"", "Cold Sign \"Insta-Freeze Beam\"", "Blowing Ice \"Ice Tornado\"", "Ice Cube \"Great Crusher\"", "Ice Sign \"Ultimate Blizzard\"", "Ice Sign \"Perfect Glacialist\"", "Ice King \"Frost King\""]
            },
            {
                "id": "3",
                "lastName": "",
                "firstName": "Sunny Milk",
                "species": "Fairy",
                "spellCards": ["Sunlight \"Sunshine Blast\"", "Light Sign \"Rutile Flection\"", "Sunfire \"Ice Dissolver\"", "Sky Sign \"Elfin Canopy\"", "Rainbow Light \"Prism Flash\"", "Light Fairy \"Diamond Ring\"", "Light Sign \"Blue Deflection\"", "Sun Sign \"Aggressive Light\"", "Sun Sign \"Direct Sunlight\"", "Flickering Light \"Fatal Flash\"", "Light Fairy \"Cross Diffusion\"", "Light Sign \"Yellow Deflection\"", "Sunlight \"Sunshine Needle\"", "Light Sign \"Hyper Inflection\"", "Sunfire \"Ice Dissolver\"", "Violent Light \"Sunburst\"", "Team Tech \"Fairy Overdrive\"", "\"Three Fairies\""]
            },
            {
                "id": "4",
                "lastName": "",
                "firstName": "Luna Child",
                "species": "Fairy",
                "spellCards": ["Moon Sign \"Lunatic Rain\"", "Moon Sign \"Luna Cyclone\"", "Moonlight \"Silent Storm\"", "Light Sign \"Bright Night\"", "Moonfire \"Ice Dissolver\"", "Sky Sign \"Break Canopy\"", "Moonlight \"Dark Stillness\"", "Hindering Light \"Moonlight Wall\"", "Night Sign \"Night Fairies\"", "Moonlight \"Silent Flower\"", "Light Sign \"Full Moon Night\"", "Moonfire \"Ice Dissolver\"", "Falling Light \"Triple Light\"", "Moonlight \"Moon Stillness\"", "Light Barrier \"Wall Break\"", "Moonlight \"Silent Cyclone\"", "Team Tech \"Fairy Overdrive\"", "\"Three Fairies\""]
            },
            {
                "id": "5",
                "lastName": "",
                "firstName": "Star Sapphire",
                "species": "Fairy",
                "spellCards": ["Shooting Star \"Petit Comet\"", "Stardust \"Sprinkle Piece\"", "Star Sign \"Twinkle Sapphire\"", "Starlight \"Star Laser\"", "Light Sign \"Triple Meteor\"", "Starfire \"Ice Dissolver\"", "Bright Star \"Orion Belt\"", "Shooting Star \"Comet Stream\"", "Stardust \"Star Piece Shower\"", "Star Sign \"Shooting Sapphire\"", "Starlight \"Star Storm\"", "Light Sign \"Extensive Meteor\"", "Starfire \"Ice Dissolver\"", "Bright Star \"Great Triangle\"", "Team Tech \"Fairy Overdrive\"", "\"Three Fairies\""]
            },
            {
                "id": "6",
                "lastName": "",
                "firstName": "Daiyousei",
                "species": "Fairy",
                "spellCards": [""]
            },
            {
                "id": "7",
                "lastName": "",
                "firstName": "Clownpiece",
                "species": "Fairy",
                "spellCards": ["Hell Sign \"Hell Eclipse\"", "Hell Sign \"Eclipse Of Hell\"", "Hell Sign \"Flash And Stripe\"", "Hell Sign \"Star And Stripe\"", "Hellfire \"Graze Inferno\"", "Hellfire \"Infernal Essence Of Grazing\"", "Inferno \"Striped Abyss\"", "\"Fake Apollo\"", "\"Apollo Hoax Theory\"", "Hell Sign \"Bursting Grudge\"", "Hell Sign \"Double Stripe\"", "Moon Dream \"Eclipse Nightmare\""]
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
            "Equips": {
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
                ],
                "Head": [
                    {
                        "id": "",

                    }],
                "Body": [
                    {
                        "id": "",

                    }],
                "Legs": [
                    {
                        "id": "",

                    }],
                "Arms": [
                    {
                        "id": "",

                    }]
            }
        },
        "Money": ["534",
            '526', "23"]

    };
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
                user: user,
                giveCharacter: user.characters[0],
                giveEquips: user.characters[0].equips
            };
        },
        methods: {

            characterChange(event) {
                this.giveEquips = this.user.characters[event].equips;
                this.giveCharacter = this.user.characters[event];
            }
        }
    }

</script>


<style src="./assets/css/skeleton.css"></style>
<style src="./assets/css/style.css"></style>