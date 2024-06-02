<script>
import GridWithCards from './GridWithCards.vue';
import dbData from '../../data/db.json'
export default{
    data(){
        return {
            products: dbData['products']
        }
    },
    components: {
        GridWithCards,
    },
    mounted(){
        console.log(this.products)
    }
}
</script>

<template>
<main>
    <div class="container">
        <GridWithCards :products="products"/>       
    </div>
</main>
</template>

<style lang="scss" scoped>
    @import "../../assets/style/partials/variables";
    
    .container{
        width: $container-width;
        margin: 0 auto;
    }
</style>