<template>
  <div id="app">
    <!-- use component -->
    <Header/>
    <!-- here we call the component main and send him the api's url -->
    <Main :url="apiUrl"/>
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
  },
  data(){
    return{
      // here we take the api URL where take the datas
      apiUrl:"https://flynn.boolean.careers/exercises/api/array/music"
    }
  }
}
</script>

<style lang="scss">

// import bootstrap
@import "~bootstrap/scss/bootstrap";

// general settings
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
body {
      background-color: hsl(209deg 33% 17%);
}

</style>
