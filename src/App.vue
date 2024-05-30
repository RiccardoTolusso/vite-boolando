<script>
import HeaderComponent from './components/header/HeaderComponent.vue';

export default {
  name:"MyApp",
  data(){
    return {

    }
  },
  components:{
    HeaderComponent,
  }
}
</script>

<template>
  <!-- header component -->
  <HeaderComponent />

  <main>
    <!-- main component -->
      <!-- grid component -->
        <!-- card component -->
  </main>

  <footer>
    <!-- footer component -->
  </footer>
</template>

<style lang="scss">
@use "./assets/style/main.scss";


</style>