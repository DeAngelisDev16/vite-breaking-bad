<script>
import { store } from '../store';
import axios from 'axios';


export default {
    name: 'AppMain',
    data() {
        return {
            store,
            cardsList: [],
        }
    },
    methods: {
        getCards() {
            const self = this;

            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0', {
                params: {
                    ID: 12345
                }
            })
                .then(function (response) {
                    console.log(response.data.data);
                    self.cardsList = response.data.data;
                })
                .catch(function (error) {
                    console.log(error);
                })
                .then(function () {
                    // always executed
                });
        }
    },
    created() {
        this.getCards()

    }

}
</script>

<template>
    <div class="cards_wrapper">
        <div class="card" v-for="card in cardsList">
            <img :src="card.card_images[0].image_url" alt="#">
            <h4>{{ card.name }}</h4>
            <p>{{ card.archetype }}</p>

        </div>
    </div>


</template>

<style lang="scss" scoped>
.cards_wrapper {
    width: 70%;
    margin: 2rem auto;
    text-align: center;
    display: flex;
    flex-wrap: wrap;

    .card {
        width: calc(100% / 5);
        padding: 1.5rem;


        img {
            width: 100%;
        }


    }

}
</style>