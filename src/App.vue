<script>
import HeaderComponent from './components/header/HeaderComponent.vue';
import MainComponent from './components/main/MainComponent.vue';

export default {
  name:"MyApp",
  data(){
    return {

    }
  },
  components:{
    HeaderComponent,
    MainComponent,
  }
}
</script>

<template>
  <!-- header component -->
  <HeaderComponent />

  <MainComponent />

  <footer>
    <!-- footer component -->
  </footer>
</template>

<style lang="scss">


</style>