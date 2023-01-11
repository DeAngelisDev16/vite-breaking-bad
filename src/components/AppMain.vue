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
            axios.get('/user', {
                params: {
                    ID: 12345
                }
            })
                .then(function (response) {
                    console.log(response);
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

    }

}
</script>

<template>
    <h2>Questo è il main</h2>


</template>

<style scoped>

</style>