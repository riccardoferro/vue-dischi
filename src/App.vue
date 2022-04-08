<template>
  <div id="app">
    <!-- use component -->
    <Header/>
    <Main />
  </div>
</template>

<script>

// imported component Header
import Header from '@/components/Header.vue'
import Main from '@/components/Main.vue'


export default {
  name: 'App',
  components: {
    //declared component
    Header,
    Main
  }
}
</script>

<style lang="scss">

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

</style>
