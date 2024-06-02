<script>
export default{
    name: "Cardbadge",
    props: [
        'badges',
        'colorsMap'
    ],
    data(){
        return {
            defaultBackground: "black"
        }
    },
    methods:{
        getColor(key){
            // controlla se esiste una colorsMap
            if(this.colorsMap){
                // controlla se la chiave esiste nella colors map
                if (this.colorsMap[key]){
                    return this.colorsMap[key]
                }
            }
            // altrimenti usa il colore di default
            return this.defaultBackground
        }
    }
}
</script>
<template>

    <div class="badges-container">
        <div class="badge" v-for="badge in badges.toReversed()" :style="{'background-color': getColor(badge.type)}">{{badge.value}}</div>       
    </div>
</template>

<style lang="scss" scoped>
@use '../../assets/style/partials/variables' as *;
.badges-container{
    position: absolute;

    .badge{
        display: inline-block;
        margin-right: 0.3rem;
        padding: 1px 10px;
        color: white;
        font-weight: bold;
        font-size: $small-text-font-size;
    }
}

</style>