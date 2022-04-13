<template>
    <!-- v-model="selectedGenre" take the value of the option selected -->
    <!-- "@change" is an event that when we select other option of the select we call a method  -->
    <select v-model="selectedGenre" @change="changeGenre">
        <option value="">All genre</option>
        <option v-for="genre in generi" :key="genre" :value="genre">
          {{genre}}
        </option>
    </select>
</template>

<script>
export default {
  name: "GenreFilter",

  // computed properties
  props: {
      generi: Array
  },

  // datas
  data(){
    return {
      // var selectedGenre settled empty, when empty we show all the cards
      selectedGenre: ""
    }
  },

  // methods
  methods: {
    // this method with emit send the value of the current var selectedGenre to the father components who is waiting
    changeGenre(){
      console.log(this.selectedGenre);
      this.$emit('changedGenre',this.selectedGenre);
    }
  }
}
</script>

<style>

</style>