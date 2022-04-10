<template>
    <main>
        <div class="container pb-5 pt-5 d-flex justify-content-center">
            <div >
                <div v-if="albums.length > 0 " class="row justify-content-between w-75 m-auto">
                  <SingleAlbum  
                  v-for="(item,index) in albums" 
                  :key="index"   
                  :album = "item" 
                  class="col-12 col-md-3 col-xl-2 "/>
                </div>
                <div v-else class="load" >
                    <LoadingComponent />
                </div>
            </div>
        </div>
    </main>
</template>

<script>
// import library axios
import axios from 'axios';
import SingleAlbum from "@/components/subcomponents/SingleAlbum.vue"
import LoadingComponent from "@/components/subcomponents/LoadingComponent.vue"


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
  components: {
    SingleAlbum,
    LoadingComponent
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
              console.log(response)
              this.albums = response.data.response
              console.log(this.albums)
          }
        }
      ).catch((error)=>{
        console.log(error);
      })
    }
  }
}
</script>

<style lang="scss" scoped>
  main {
    background-color: hsl(209deg 33% 17%);
    .load {
      height: 90vh;
    }
  }
</style>