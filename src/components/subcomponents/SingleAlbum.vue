<template>
    <div class="card-rf me-1" >
        <img :src="album.poster" :alt="album.title" class="img-fluid pb-4">
        <h5>{{album.title}}</h5>
        <span>{{album.author}}</span>
        <span class="d-block">{{album.year}}</span>
    </div>
</template>

<script>
export default {
/*
author: "Bon Jovi"
genre: "Rock"
poster: "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg"
title: "New Jersey"
year: "1988"
*/
  name: "AlbumSingle",
  props: {
    album: Object
  },
}

</script>

<style lang="scss" scoped>



.card-rf {
  text-align: center;
  margin-top: 20px;
  padding: 20px;
  background-color: hsl(210deg 21% 23%);
  h5 {
    text-transform: uppercase;
    color: white;
  }
  span {
    color: hsl(33deg 5% 42%);
    font-size: 12px;
  }
}
</style>