<template>
  <div class="container">
    <MovieLists :movies="movies" />
  </div>
</template>

<script>
import MovieLists from "./components/MovieLists.vue";
import data from "../data";

export default {
  name: "App",
  data() {
    return {
      movies: data,
    };
  },
  components: {
    MovieLists,
  },
  async created() {
    try {
      const url = "https://jsonkeeper.com/b/WTPZ";
      const response = await fetch(url, {
        // headers: {
        //   'Access-Control-Allow-Origin': '*'
        // }
});
      if (response.ok) {
        this.movies = await response.json();
      }
    } catch (error) {
      console.log(error);
    }
  },
  // It worked when hadn't blocked by cors
};
</script>

<style>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: black;
  color: whitesmoke;
}
</style>
