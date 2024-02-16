<template>
   <ul class="movie-list list-group">
      <MovieListItme v-for="movies in movies" :movies="movies" @onToogle="$emit('onToogle',$event)" @deleteItme="$emit('deleteItme',movies.id)" :key="movies.id" />
   </ul>
</template>
<script>
import MovieListItme from "../movie-list-itme/MovieListItme.vue";
export default {
   components: { MovieListItme },
   props: {
      movies: {
         type: Object,
         required: true,
      },
   },
};
</script>
<style>
.movie-list {
   margin-top: 2rem;
   padding: 1.5rem;
   background-color: #fcfaf5;
   border-radius: 5px;
   box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.5);
}
</style>
