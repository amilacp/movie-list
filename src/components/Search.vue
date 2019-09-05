<template>
  <div class="search-container">
    <b-container>
      <b-nav-form>
        <b-form-input size="sm" class="mr-sm-2" placeholder="Search for a movie" v-model="movie"></b-form-input>
        <b-button size="sm" class="my-2 my-sm-0" type="submit" @click.prevent="getMovie">Search</b-button>
      </b-nav-form>
    </b-container>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      movie: ""
    };
  },
  methods: {
    getMovie() {
        axios
              .get("https://api.themoviedb.org/3/movie/popular", config)
              .then(res => (this.movies = res.data.results))
              .catch(err => console.log(err));
    }
  }
};
</script>
<style scoped>
.search-container {
  padding-bottom: 20px;
}
</style>