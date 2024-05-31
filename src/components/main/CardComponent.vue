<script>
export default{
    name:"card",
    props: ['img'],
    methods:{
        secondaryImage(event){
            event.target.childNodes[0].src = `/img/${this.img}b.webp`
        },
        primaryImage(){
            event.target.childNodes[0].src = `/img/${this.img}.webp`
        }
    }

}
</script>

<template>
    <div @mouseenter="secondaryImage" @mouseleave="primaryImage">
        <img :src="`/img/${img}.webp`" :alt="`Immagine ${img}`">
        <h2>Titolo</h2>
        <h5>Descrizione del prodotto</h5>
    </div>
</template>

<style lang="scss" scoped>
    @import "../../assets/style/partials/variables";
    
    div{
        width: $col-width;
        margin: 30px 0;
        img{
            width: 100%;
        }
    }
</style>