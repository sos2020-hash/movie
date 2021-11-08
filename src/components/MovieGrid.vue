<template>
  <div class="grid-item">
    <div class="img-container">
      <img :src="movie.poster ? movie.poster : image" :alt="movie.name" />
    </div>
    <div>
      <h4 class="name">{{ movie.name }}</h4>
    </div>
    <div>
      <ul class="movie-status">
        <li>
          <i class="far fa-star"><span class="info">{{ movie.rating.toFixed(1) }}</span></i>
        </li>
        <li>
          <i class="far fa-heart"><span class="info">{{ movie.likeCount }}</span></i>
        </li>
        <li>
          <i class="far fa-comment-alt"><span class="info">{{ movie.reviewCount }}</span></i>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import image from "../assets/no-poster-available.png";

export default {
  name: "MovieGrid",
  props: {
    movie: Object,
  },
  data() {
    return {
      image: image,
    };
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
  max-width: 12rem;
}

.movie-status {
  display: flex;
  justify-content: space-evenly;
  list-style-type: none;
  padding: 0;
}

.movie-status li {
  margin-right: 10px;
}

.name {
  margin: 10px;
}

.info {
  color: gold;
}
</style>
