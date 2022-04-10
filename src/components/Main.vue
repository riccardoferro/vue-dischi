<template>
    <main>
        <div class="container">
            <div class="row">
              <div class="col-12 col-md-6 col-xl-3">
                <SingleAlbum />
              </div>
            </div>
        </div>
    </main>
</template>

<script>
// import library axios
import axios from 'axios';
import SingleAlbum from "@/components/subcomponents/SingleAlbum.vue"

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
    SingleAlbum
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
    height: 90vh;
  }
  

</style>