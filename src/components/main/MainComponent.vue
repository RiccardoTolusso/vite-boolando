<script>
import GridWithCards from './GridWithCards.vue';

export default{
    data(){
        return {
            products:[
                {
                    img: 1,
                },
                {
                    img: 2,
                },
                {
                    img: 3,
                },
                {
                    img: 4,
                },
                {
                    img: 5,
                },
                {
                    img: 6,
                },
            ]
        }
    },
    components: {
        GridWithCards,
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