<template>
  <b-container>
    <div v-if="movies.length">
      <b-row>
        <div v-for="movie in movies " v-bind:key="movie.id">
          <Movie v-bind="movie" :movie="movie" />
        </div>
      </b-row>
    </div>
    <div v-else>
      <h5>No movies available yet 😢</h5>
    </div>
  </b-container>
</template>

<script>
import Movie from "./Movie.vue";
export default {
  name: "MovieList",
  props: ["movies"],
  components: {
    Movie
  }
};
</script>

<style>
</style>