<template>
    <main>
        <!-- Here we have the select input that filter the albums by gender -->
        <div class="container ">
            <div class="row w-75 pt-2 m-auto c-white text-center">
                    <!-- Call sub-component with a waiting event and we send him "generi='genres'"
                        where genres is a computed propertie, scroll down to see 
                     -->
                    <FilterGenre @changedGenre="performfilteredGenres" :generi="genres"/>
            </div>
        </div>

        <!-- Albums with their info -->
        <div class="container pb-1 pt-1 d-flex justify-content-center">
            <div v-if="albums.length > 0" class="row gap-2 w-75 m-auto">
              <!-- We had created a sub-component where we send the single album " :album='item' " -->
              <SingleAlbum  
              v-for="(item,index) in filteredGenres" 
              :key="index"   
              :album = "item" 
              class="col-12 col-md-3 col-xl-2 "/>
            </div>

            <!-- Here we insert an v-else, till the albums are not shown we show an custom loader -->
            <div v-else class="load" >
                <LoadingComponent />
            </div>
        </div>
    </main>
</template>


<script>
// import library axios
import axios from 'axios';

// import sub-components
import SingleAlbum from "@/components/subcomponents/SingleAlbum.vue"
import LoadingComponent from "@/components/subcomponents/LoadingComponent.vue"
import FilterGenre from "@/components/subcomponents/FilterGenre.vue"


export default {
  name: "ComponentMain",
  
  // datas
  data(){
    return {
      // created array albums where we gonna put the datas
      albums:[],

      //here we have a var settle to empty
      selectedGenre: ""
    }
  },
  // computed properties
  computed: {

      // here with the function genres we eliminate duplicates from the albums and take only the unique gender of the albums
      genres(){
        //other way to take only the genre we need in the filter
        // const uniqueGenres = [];
        // this.albums.forEach((item)=>{
        //   if (!uniqueGenres.includes(item.genre)){
        //     uniqueGenres.push(item.genre);
        //   }
        // })
        // console.log(genres);

        //trick to eliminate duplicate
        const genres = this.albums.map((album) => album.genre);
        const uniqueGenres = [...new Set(genres)];
        console.log(uniqueGenres)
        return uniqueGenres;
      },

      // this function filtered the albums by selectedGenre
      filteredGenres(){
        // if empty select all
        if (this.selectedGenre === ""){
          return this.albums;
        }
        // else select the selectedGenre
        return this.albums.filter(album => album.genre === this.selectedGenre);
      }
  },

  //here we gonna take the url API
  props: {
    url: String
  },
  
  components: {
    SingleAlbum,
    LoadingComponent,
    FilterGenre
  },
  // when the software si ready go with this first method
  mounted() {
    this.loadData();
  },

  methods: {
    // this function add elements of the APIs in our empty var album
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
      // here we catch an error if we have
      ).catch((error)=>{
        console.log(error);
      })
    },

    // this method take as a parametrer the value of the emit, in this selectGenre that we put in our
    // var empty that is call in the same way
    performfilteredGenres(selectGenre) {
        this.selectedGenre = selectGenre;
    }
  }
}
</script>

<style lang="scss" scoped>
    main {
      .load {
        height: 90vh;
      }
    }
    .c-white {
      color: white;
    }
</style>