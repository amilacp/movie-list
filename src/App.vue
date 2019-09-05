<template>
  <div id="app" class="n-container">
    <Search />
    <MovieList v-bind:movies="movies" />
  </div>
</template>

<script>
import MovieList from "./components/MovieList.vue";
import Search from "./components/Search.vue";
import axios from "axios";

export default {
  name: "app",
  components: {
    MovieList,
    Search
  },
  data() {
    return {
      movies: [],
      theToken: ""
    };
  },
  methods: {
    requestToken() {
      axios
        .get(
          "https://api.themoviedb.org/3/authentication/token/new?api_key=6ed12e064b90ae1290fa326ce9e790ff"
        )
        .then(
          function(resp) {
            if (typeof resp.data == "string") {
              resp.data = JSON.parse(resp.data);
            }
            let theToken = resp.data;
          }.bind(this)
        );
    }
  },
  created() {
    var token = this.requestToken();
    var config = {
      headers: { Authorization: "bearer " + token }
    };
    axios
      .get("https://api.themoviedb.org/3/movie/popular", config)
      .then(res => (this.movies = res.data.results))
      .catch(err => console.log(err));
  }
};
</script>


<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 70px0px;
}
</style>
