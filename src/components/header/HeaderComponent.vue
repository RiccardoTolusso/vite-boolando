<script>
import NavBarButton from './NavBarButton.vue';

export default {
    name:"Header",
    methods:{

    },
    components:{
        NavBarButton,
    }
}
</script>

<template>
    <header>
        <div class="container">
            <div class="left">
                <NavBarButton text="Donna"/>
                <NavBarButton text="Uomo"/>
                <NavBarButton text="Bambini"/>
            </div>
            <!-- logo -->
            <img src="../../../public/img/boolean-logo.png" alt="Boolean Logo">
            <div class="right">
                <!-- TODO: add icons -->
                <NavBarButton text="Donna"/>
                <NavBarButton text="Uomo"/>
                <NavBarButton text="Bambini"/>
            </div>
        </div>
    </header>
</template>

<style lang="scss" scoped>
@import "../../assets/style/partials/variables";

header{
    background-color: $primary-color;

    div{
        display: flex;
        gap: 10px;
        &.container{
            width: $container-width;
            margin: 0 auto;
            justify-content: space-between;
            align-items: center;
        }
        
        
    }

    img{
        height: 45px;
        padding: 10px 0;
    }
}

</style>