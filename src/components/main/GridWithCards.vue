<script>
import CardComponent from './CardComponent.vue';

export default{
    name: "grid",
    components: {
        CardComponent,
    },
    props:[
        'products'
    ], 
    methods:{
        toggleFavourite(product){
            product.isInFavorites = !product.isInFavorites
        }
    }
}
</script>

<template>
<div class="grid">
    <CardComponent v-for="product in products" :product="product" @click="toggleFavourite(product)"></CardComponent>
</div>
</template>

<style lang="scss" scoped> 
@import "../../assets/style/partials/variables";

.grid{
    gap: 10px;
    display: flex;
    flex-wrap: wrap;
}

</style>