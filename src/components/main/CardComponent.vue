<script>
export default{
    name:"card",
    props: ['img'],
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
            this.setImageAfter(event, `/img/${this.img}b.webp`, 0.1)
            
            
        },
        primaryImage(event){
            this.clearTimeout()
            this.setImageAfter(event, `/img/${this.img}.webp`, 0.1)
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