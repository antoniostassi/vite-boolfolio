<script>



export default {
  data() {
    
  },
  // 2) Dichiarazione del componente

}
</script>

<template>
  <div class="bg-grey">
    <router-view></router-view>
  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
// Import all of Bootstrap's CSS
@import "bootstrap/scss/bootstrap";
  .bg-grey{
    background-color:lightgrey;
    height:100vh;
  }
</style>
