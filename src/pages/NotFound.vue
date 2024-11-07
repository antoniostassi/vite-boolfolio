<script>
import AppHeader from '../components/AppHeader.vue';

import AppFooter from '../components/AppFooter.vue';


export default {
  data() {
    
  },
  components: {
    AppHeader,

    AppFooter
  },
}
</script>


<template>
    <AppHeader />
        
    <div class="container">
        <h1 class="fs-5">
            404: Pokemon non trovato
        </h1>
    </div>

    <AppFooter />
</template>
  
<style lang="scss" scoped>

</style>