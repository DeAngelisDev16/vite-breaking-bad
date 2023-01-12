<script>
import { store } from '../store';



export default {
    name: 'SelectComponent',
    data(){
        return{
            store,
        }
    }
  
}
</script>

<template>
    <div class="select_container">
        <label for="" class="form-label">Archetypes</label>
        <select @change="$emit('changed')" v-model="store.searchArchetype" name="" id="">
            <option selected>Select one</option>
            <option  value="Alien">Alien</option>
            <option  value="Laval">Laval</option>
            <option  value="Vylon">Vylon</option>
            <option  value="Inzektor">Inzektor</option>
            <option  value="Umi">Umi</option>
            <option  value="Gusto">Gusto</option>
            

        </select>
    </div>
    
    

  


</template>

<style lang="scss" scoped>
.select_container{
    padding: 1rem;
}

</style>