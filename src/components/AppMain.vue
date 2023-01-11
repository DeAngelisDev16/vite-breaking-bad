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

            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0', {
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
    <div class="cards_container">
        <div v-for="card in cardsList">{{ card.name }}</div>
    </div>


</template>

<style lang="scss" scoped>
.cards_container {
    width: 70%;
    margin: 2rem auto;
    text-align: center;

}
</style>