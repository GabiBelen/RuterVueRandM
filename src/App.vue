<template>
  <Cards/>
  <router-view/>
</template>

<script> 
import Cards from './components/Cards.vue';
export default {
  components: {
    Cards
  }
}
</script>

<style scoped>
* {
background: rgba(250, 233, 0, 0.548)

}

</style>

