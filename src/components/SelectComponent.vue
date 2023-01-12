<script>



export default {
    name: 'SelectComponent',
  
}
</script>

<template>
    <div class="select_container">
        <label for="" class="form-label">Archetypes</label>
        <select  name="" id="">
            <option selected>Select one</option>
            <option @change="$emit('canaleAlien')" value="">Alien</option>
            <option @change="$emit('canaleLaval')" value="">Laval</option>
            <option @change="$emit('canaleVylon')" value="">Vylon</option>
            <option @change="$emit('canaleInzektor')" value="">Inzektor</option>
            <option @change="$emit('canaleUmi')" value="">Umi</option>
            <option @change="$emit('canaleGusto')" value="">Gusto</option>
            

        </select>
    </div>
    
    

  


</template>

<style lang="scss" scoped>
.select_container{
    padding: 1rem;
}

</style>