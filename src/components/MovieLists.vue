<template>
  <button @click="onSwitch" class="btn"><i class="fas fa-th"></i></button>
  <div v-if="isGrid" class="grid-container">
    <div :key="movie.uuid" v-for="movie in movies">
      <MovieGrid :movie="movie" />
    </div>
  </div>
  <div v-else class="list-container">
    <div :key="movie.uuid" v-for="movie in movies">
      <MovieList :movie="movie" />
    </div>
  </div>
</template>

<script>
import MovieGrid from "./MovieGrid.vue";
import MovieList from "./MovieList.vue";

export default {
  name: "MovieLists",
  props: {
    movies: Array,
  },
  components: {
    MovieGrid,
    MovieList,
  },
  data: function () {
    return {
      isGrid: true,
    };
  },
  methods: {
    onSwitch() {
      this.isGrid = !this.isGrid;
    },
  },
};
</script>

<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.list-container {
  display: flex;
  flex-direction: column;
}

.btn {
  position: relative;
  display: inline-flex;
  width: 180px;
  height: 55px;
  margin: 0 15px;
  perspective: 1000px;
  cursor: pointer;
}
.btn i {
  font-size: 19px;
  letter-spacing: 1px;
  transform-style: preserve-3d;
  transform: translateZ(-25px);
  transition: transform 0.25s;
  font-family: "Montserrat", sans-serif;
}
.btn i:before,
.btn i:after {
  position: absolute;
  content: "SWITCH";
  height: 55px;
  width: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 5px solid black;
  box-sizing: border-box;
  border-radius: 5px;
}
.btn i:before {
  color: #fff;
  background: #000;
  transform: rotateY(0deg) translateZ(25px);
}
.btn i:after {
  color: #000;
  transform: rotateX(90deg) translateZ(25px);
}
.btn i:hover {
  transform: translateZ(-25px) rotateX(-90deg);
}
</style>
