<script>
export default{
    name:"card",
    props: ['product'],
    data(){
        return {
            timeout: null
        }
    },
    methods:{
        clearTimeout(){
            if(this.timeout){
                clearTimeout(this.timeout)
            }
        },
        setImageAfter(event, img, after){
            this.timeout = setTimeout(() => {
                event.target.childNodes[0].src = img
            }, after*1000)
        },
        secondaryImage(event){
            this.clearTimeout()
            this.setImageAfter(event, `/img/${this.product.backImage}`, 0.1)
            
            
        },
        primaryImage(event){
            this.clearTimeout()
            this.setImageAfter(event, `/img/${this.product.frontImage}`, 0.1)
        },
        isDiscount(product){
            if(product.badges){
                for (const badge of product.badges){
                    const badgeValues = Object.values(badge)
                    if(badgeValues){
                        for (const value of badgeValues){
                            if (value === "discount"){
                                return true;
                            }
                        }
                    }
                }
            } 
            return false;
        },
        fullPrice(product){
            let discount
            for (const badge of product.badges){
                if (badge.type === 'discount'){
                    discount = 1 +  Math.abs(parseInt(badge.value))/100
                }
            }
            console.log(discount)
            return (product.price * discount).toFixed(2)
            
        }
    }

}
</script>

<template>
    <div class="card" @mouseenter="secondaryImage" @mouseleave="primaryImage">
        <img :src="`/img/${product.frontImage}`" :alt="`Immagine ${product.brand} ${product.name}`">
        <div class="brand">{{product.brand}}</div>
        <div class="name">{{product.name}}</div>
        <span class="price">{{ product.price }} &euro;</span><span class="fullprice" v-if="isDiscount(product)">{{ fullPrice(product) }} &euro;</span>
    </div>
</template>

<style lang="scss" scoped>
    @import "../../assets/style/partials/variables";
    
    .card{
        width: $col-width;
        margin: 30px 0;
        img{
            width: 100%;
        }

        .brand{
            font-size: $small-text-font-size;
        }
        .name{
            font-size: $big-text-font-size;
            text-transform: uppercase;
            font-weight: bold;
        }

        .price{
            font-size: $small-text-font-size;
            color: $color-red;
            font-weight: bold;
        }
        .fullprice{
            font-size: $small-text-font-size;
            text-decoration: line-through;
            margin-left: 0.3rem;
        }
    }
</style>