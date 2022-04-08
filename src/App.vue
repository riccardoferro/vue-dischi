<template>
  <div id="app">
    <!-- use component -->
    <Header/>
  </div>
</template>

<script>

// imported component Header
import Header from '@/components/Header.vue'

export default {
  name: 'App',
  components: {
    //declared component
    Header
  }
}
</script>

<style lang="scss">



</style>
