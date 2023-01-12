<script>
import { store } from '../store';
import axios from 'axios';
import SelectComponent from './SelectComponent.vue';


export default {
    name: 'AppMain',
    components: {
        SelectComponent,
    },
    data() {
        return {
            store,
            cardsList: [],
            apiUrl: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0',

        }
    },
    methods: {
        getCards() {
            const self = this;

            axios.get(this.apiUrl, {
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
        },

        searchCard() {
            this.getCards();
        }


    },
    created() {
        this.getCards()

    }

}
</script>

<template>
    <main>
        <SelectComponent @changed="searchCard()" />



        <div class="result_banner">
            <p>Found {{ cardsList.length }} cards</p>
        </div>
        <div class="cards_wrapper">
            <div class="card" v-for="card in cardsList">
                <img :src="card.card_images[0].image_url" alt="#">
                <div class="card_info">
                    <h5>{{ card.name }}</h5>
                    <p>{{ card.archetype }}</p>

                </div>

            </div>
        </div>

    </main>


</template>

<style lang="scss" scoped>
main {
    background-color: orange;
    padding-top: 3rem;
}

.result_banner {
    margin: auto;
    width: 70%;
    height: 50px;
    color: white;
    background-color: black;
    display: flex;
    align-items: center;

    p {
        padding: 1rem;
    }

}

.cards_wrapper {
    width: 70%;
    margin: auto;
    text-align: center;
    display: flex;
    flex-wrap: wrap;
    background-color: white;
    padding: 2rem;


    .card {
        width: calc(100% / 5);

        padding: 1.5rem;



        img {
            width: 100%;
        }

        .card_info {
            height: 120px;
            background-color: orange;
            margin-top: -5px;

            h5,
            p {
                text-transform: uppercase;
                padding-top: 1rem;

            }


        }

        .card_info h5 {
            color: white;
        }




    }

}
</style>