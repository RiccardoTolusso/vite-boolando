<script>
import CardBadgeComponent from './CardBadgeComponent.vue'

export default{
    name: "card",
    props: ['product'],
    components: [CardBadgeComponent],
    data() {
        return {
            timeout: null,
            colorsMap: {
                'discount': 'red',
                'tag': 'green'
            }
        };
    },
    methods: {
        clearTimeout() {
            if (this.timeout) {
                clearTimeout(this.timeout);
            }
        },
        setImageAfter(event, img, after) {
            this.timeout = setTimeout(() => {
                event.target.childNodes[0].src = img;
            }, after * 1000);
        },
        secondaryImage(event) {
            // dopo 100 millisecondi imposta l'immagine a quella secondaria
            this.clearTimeout();
            this.setImageAfter(event, `/img/${this.product.backImage}`, 0.1);
        },
        primaryImage(event) {
            // dopo 100 millisecondi imposta l'immagine a quella principale
            this.clearTimeout();
            this.setImageAfter(event, `/img/${this.product.frontImage}`, 0.1);
        },
        isDiscount(product) {
            // controlla se c'è uno sconto applicato all'articolo
            if (product.badges) {
                for (const badge of product.badges) {
                    const badgeValues = Object.values(badge);
                    if (badgeValues) {
                        for (const value of badgeValues) {
                            if (value === "discount") {
                                return true;
                            }
                        }
                    }
                }
            }
            return false;
        },
        fullPrice(product) {
            // in caso di sconto applicato calcola il prezzo prima dello sconto
            let discount;
            for (const badge of product.badges) {
                if (badge.type === 'discount') {
                    discount = 1 + Math.abs(parseInt(badge.value)) / 100;
                }
            }
            return (product.price * discount).toFixed(2);
        },
        heartColor(product){
            if (product.isInFavorites){
                return "red";
            } else {
                return "black"
            }
        }

    },
    components: { CardBadgeComponent }
}
</script>

<template>
    <div class="card liked" @mouseenter="secondaryImage" @mouseleave="primaryImage">
        <div class="heart" :style="{'color': heartColor(product)}">
            <i class="fa-solid fa-heart"></i>
        </div>
        <img :src="`/img/${product.frontImage}`" :alt="`Immagine ${product.brand} ${product.name}`">
        <CardBadgeComponent :badges="product.badges" :colors-map="colorsMap"/>
        <div class="brand">{{product.brand}}</div>
        <div class="name">{{product.name}}</div>
        <span class="price">{{ product.price }} &euro;</span><span class="fullprice" v-if="isDiscount(product)">{{ fullPrice(product) }} &euro;</span>
    </div>
</template>

<style lang="scss" scoped>
    @import "../../assets/style/partials/variables";
    
    .card{
        position: relative;
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

        // BADGES
        .badges-container{    
           transform: translateY(-40px);
        }

        .heart{
            position: absolute;
            right: 0;
            top: 5px;
            padding: 1px 5px;
            background-color: white;
        }
    }
</style>