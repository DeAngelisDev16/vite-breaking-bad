<script>
import { store } from '../store';
import axios from 'axios';


export default {
    name: 'AppMain',
    data() {
        return {
            store,
        }
    },
    methods: {
        getCards() {
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0', {
                params: {
                    ID: 12345
                }
            })
                .then(function (response) {
                    console.log(response.data);
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
    <h2>Questo è il main</h2>


</template>

<style scoped>

</style>