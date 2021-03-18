<template>
    <div class="about">
        <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.4.1/css/all.css" integrity="sha384-5sAR7xN1Nv6T6+dT2mhtzEpVJvfS3NScPQTrOxhwjIuvcA67KV2R5Jz6kr4abQsz" crossorigin="anonymous">

        <div class="head">
            <div class="break"></div>
            <img alt="tourney" src="../assets/tourney.jpg">
            <h1>ATP Tournaments (2017)</h1>
            <div class="break small"></div>
        </div>
        <div class="tourneys">
            <div class="tourney" v-for="tourney in tourneys" v-bind:key="tourney.tourney_id">
                <div v-if="tourney.is_fav === 'true'">
                    <i class="fas fa-star fa-lg" v-on:click="favorite(tourney.tourney_id)"></i>
                    
                </div>
                <div v-else>
                    <i class="far fa-star fa-lg" v-on:click="favorite(tourney.tourney_id)"></i>
                </div>
                <br />
                <h2>{{tourney.tourney_name}}</h2>
                <h3><em>Singles champion:</em> {{tourney.singles_winner_name}}</h3>
                <h3><em>Doubles champions:</em> {{tourney.doubles_winner_1_name}} and {{tourney.doubles_winner_2_name}}</h3>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
        computed: {
            tourneys() {
                console.log(this.$root.$data.tourneys);
                return this.$root.$data.tourneys;
            }
        },
        methods: {
            favorite(key) {
                for (let i = 0; i < this.$root.$data.tourneys.length; ++i) {
                    if (this.$root.$data.tourneys[i].tourney_id === key) {
                        if (this.$root.$data.tourneys[i].is_fav === 'true') {
                            this.$root.$data.tourneys[i].is_fav = 'false';
                            for (let j = 0; j < this.$root.$data.favs.length; ++j) {
                                if (this.$root.$data.favs[j].tourney_id === key) {
                                    this.$root.$data.favs.splice(j, 1);
                                    break;
                                }
                            }
                            break;
                        }
                        else {
                            this.$root.$data.tourneys[i].is_fav = 'true';
                            this.$root.$data.favs.push(this.$root.$data.tourneys[i]);
                        }
                    }
                }
            }
        }
    }
</script>

<style>
    .fas {
        color: #e29d0f;
    }

    .fa-star {
        float: right;
        margin-top: 10px;
    }

    .break {
        height: 20px;
        display: block;
    }

    .small {
        height: 10px;
    }

    .head {
        background-color: white;
        margin: 0;
    }

    .about {
        background-color: white;
        padding: 0 25px;
    }

        .about img {
            margin-left: 40%;
            margin-right: 40%;
            width: 20%;
            height: 20%;
        }

    .tourneys {
        display: grid;
        grid-template: auto auto auto auto auto / 1fr 1fr 1fr 1fr 1fr;
        column-gap: 15px;
        grid-row-gap: 15px;
        background-color: white;
    }

    @media(max-width: 1500px) {
        .tourneys {
            grid-template: auto auto auto auto / 1fr 1fr 1fr 1fr;
        }
    }

    @media(max-width: 1200px) {
        .tourneys {
            grid-template: auto auto auto / 1fr 1fr 1fr;
        }
    }

    @media(max-width: 900px) {
        .tourneys {
            grid-template: auto auto / 1fr 1fr 1fr;
        }
    }

    @media(max-width: 600px) {
        .tourneys {
            grid-template: auto / 1fr;
        }
    }

    .tourney {
        outline: solid;
        outline-color: #e29d0f;
        margin: 5px;
        padding-left: 5px;
        padding-right: 5px;
    }

    h2 {
        text-align: center;
        text-decoration: underline;
        font-size: large;
    }

    h3 {
        font-size: medium;
    }

    h4 {
        font-size: small;
    }

    em {
        text-decoration: underline;
    }
</style>
