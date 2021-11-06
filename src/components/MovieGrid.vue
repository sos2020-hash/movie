<template>
  <div class="grid-item">
    <div class="img-container">
      <img v-bind:src="movie.poster" alt="{{movie.name}}" />
    </div>
    <div>
      <h3>{{ movie.name }}</h3>
    </div>
    <div>
      <ul class="movie-status">
        <li>
          <i class="far fa-star">{{ movie.rating.toFixed(1) }}</i>
        </li>
        <li>
          <i class="far fa-heart">{{ movie.likeCount }}</i>
        </li>
        <li>
          <i class="far fa-comment-alt">{{ movie.reviewCount }}</i>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieGrid",
  props: {
    movie: Object,
  },
};
</script>

<style scoped>
img {
  max-width: 100%;
  max-height: 100%;
}

.grid-item {
  padding: 10px;
}

.movie-status {
  display: flex;
  justify-content: space-evenly;
  list-style-type: none;
}

.movie-status li {
  margin-right: 10px;
}
</style>
