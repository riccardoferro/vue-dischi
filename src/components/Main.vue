<template>
    <main>
    </main>
</template>

<script>
// import library axios
import axios from 'axios';

export default {
  name: "ComponentMain",
  data(){
    return {
      // created array albums where we gonna put the datas
      albums:[]
    }
  },
  //here we gonna take the url API
  props: {
    url: String
  },
  // when the software si ready go with this first function
  mounted() {
    this.loadData();
  },
  methods: {
    loadData(){
      // here we gonna ask for a response from the api
      axios.get(this.url).then(
        (response)=> {
          // if response good
          if (response.status === 200) {
              this.albums = response.data
              console.log(this.albums)
          }
        }
      )
    }
  }
}
</script>

<style lang="scss" scoped>
  main {
    background-color: hsl(209deg 33% 17%);
    height: 90vh;
  }
  
</style>