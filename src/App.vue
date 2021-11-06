<template>
  <div class="container">
    <MovieLists :movies="movies" />
  </div>
</template>

<script>
import MovieLists from "./components/MovieLists.vue";

export default {
  name: "App",
  data() {
    return {
      movies: [
        {
          uuid: "cbf06196-18e3-40ae-8381-4a615749492b",
          name: "盛夏友晴天",
          openDate: 1624464000,
          poster:
            "https://storage.movie6.com/movie/4a27e_Luca_HKPoster_20210603_1622786940.jpg",
          rating: 3.888888888888888,
          likeCount: 372,
          reviewCount: 36,
          duration: 96,
        },
        {
          uuid: "4d5818ca-e466-4892-94ad-313a5b265516",
          name: "比得兔2 : 走佬日記",
          openDate: 1625068800,
          poster:
            "https://storage.movie6.com/movie/4e74d_PeterRabbit2Poster_1620287051.jpg",
          rating: 4.125,
          likeCount: 312,
          reviewCount: 4,
          duration: 93,
        },
        {
          uuid: "f2290c6a-dd83-4244-a881-33f0bb5cd05b",
          name: "國定殺戮日：無限狂屠",
          openDate: 1625068800,
          poster:
            "https://storage.movie6.com/movie/3f395_FOREVERPURGEHKonesheet_1_cowboy__1622707583.jpg",
          rating: 3.952380952380953,
          likeCount: 156,
          reviewCount: 21,
          duration: 0,
        },
      ],
      error: null,
    };
  },
  components: {
    MovieLists,
  },
  beforeMount() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const url = "https://jsonkeeper.com/b/WTPZ";
      const res = await fetch(url, {
        method: "GET",
        mode: "no-cors",
      });
      if (res.ok) {
        const result = await res.json();
        return (this.movies = result);
      }
    },
  },
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
  margin-top: 60px;
}
</style>
