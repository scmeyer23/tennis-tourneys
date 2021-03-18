<template>
    <div class="about">
        <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.4.1/css/all.css" integrity="sha384-5sAR7xN1Nv6T6+dT2mhtzEpVJvfS3NScPQTrOxhwjIuvcA67KV2R5Jz6kr4abQsz" crossorigin="anonymous">

        <div class="head">
            <div class="break"></div>
            <img alt="tourney" src="../assets/fav.png">
            <h1>Your Favorite Tournaments ({{fav_number}})</h1>
            <div class="break small"></div>
        </div>
        <div class="favorites">
            <div v-if="empty">
                <h3 class="no_favs">Your favorites list is currently empty. Please go back to the "Tournaments" tabs so that you can select your favorite tournaments. Once you have done so you will see them here with more information than initially provided.</h3>
            </div>
            <div v-else>
                <div class="columns">
                    <div class="tourney favs" v-for="tourney in favs" v-bind:key="tourney.tourney_id">
                        <i class="fas fa-star fa-lg" v-on:click="favorite(tourney.tourney_id)"></i>
                        <br />
                        <h2>{{tourney.tourney_name}}</h2>
                        <div class="info">
                            <div class="old">
                                <h3><em>Singles champion:</em> {{tourney.singles_winner_name}}</h3>
                                <h3><em>Doubles champions:</em> {{tourney.doubles_winner_1_name}} and {{tourney.doubles_winner_2_name}}</h3>
                            </div>
                            <div class="new">
                                <h3><em>Start date:</em> {{tourney.tourney_dates}}</h3>
                                <h3><em>Location:</em> {{tourney.tourney_location}}</h3>
                                <h3><em>Surface:</em> {{tourney.tourney_surface}}</h3>
                                <h3><em>Draw sizes:</em> {{tourney.tourney_doubles_draw}}</h3>
                                <h3><em>Prize money:</em> {{tourney.tourney_fin_commit}}</h3>
                            </div>
                            <br />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        computed: {
            favs() {
                return this.$root.$data.favs;
            },
            empty() {
                if (this.$root.$data.favs.length > 0) {
                    return false;
                }
                return true;
            },
            fav_number() {
                return this.$root.$data.favs.length;
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
    .info {
        display: grid;
        grid-template: auto auto / 2fr 1fr;
        padding-left: 10px;
    }

    .columns {
        display: grid;
        grid-template: auto auto / 1fr 1fr;
        column-gap: 15px;
    }

    .favs.tourney {
        margin-bottom: 20px;
    }

    .break {
        display: block;
        height: 10px;
    }

    @media(max-width: 1500px) {
        .columns {
            grid-template: auto / 1fr;
        }
    }

    @media(max-width: 900px) {
        .info {
            grid-template: auto / 1fr;
        }
    }
</style>
