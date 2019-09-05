<template>
  <b-col l="4">
    <b-card
      v-bind:title="movie.title"
      v-bind:img-src="poster(movie.poster_path)"
      img-alt="Image"
      img-top
      tag="article"
      style="max-width: 20rem;"
      class="mb-2"
    >
      <b-card-text>{{ `${movie.overview.slice(0,100)}...` }}</b-card-text>
      <b-button href="#" variant="primary">View more</b-button>
    </b-card>
  </b-col>
</template>

<script>
export default {
  name: "Movie",
  props: ["movie"],
  methods: {
    poster(thePath) {
      return "https://image.tmdb.org/t/p/w600_and_h900_bestv2" + thePath;
    },
    backdrop(backdropPath) {
      return "https://image.tmdb.org/t/p/w500" + backdropPath;
    }
  }
};
</script>

<style scoped>
.card-text{
  text-align: left;
}
</style>