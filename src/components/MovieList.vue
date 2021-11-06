<template>
  <div class="list-item-container">
    <div class="img-container">
      <img v-bind:src="movie.poster" alt="{{movie.name}}" />
    </div>
    <div class="movie-rating-container">
      <div class="rating">{{ movie.rating.toFixed(1) }}</div>
      <div class="rating-bar">
        <star-rating
          :rating="Number(movie.rating.toFixed(1))"
          :round-start-rating="false"
          :read-only="true"
          :show-rating="false"
          :star-size="25"
        ></star-rating>
      </div>
    </div>
    <div class="movie-info-container">
      <h2>{{ movie.name }}</h2>
      <div class="movie-info-comment">
        <div><i class="far fa-heart"></i>{{ movie.likeCount }}</div>
        <div><i class="far fa-comment-alt"></i>{{ movie.reviewCount }}</div>
      </div>
      <div>{{ new Date(movie.openDate).toLocaleDateString() }}</div>
    </div>
  </div>
</template>

<script>
import StarRating from "vue-star-rating";

export default {
  name: "MovieList",
  props: {
    movie: Object,
  },
  components: { StarRating },
};
</script>

<style scoped>
img {
  max-width: 100%;
  max-height: 100%;
}

.list-item-container {
  display: flex;
  max-height: 10rem;
}

.list-item-container .img-container {
  flex: 1;
}

.list-item-container .movie-rating-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex: 1;
}

.list-item-container .movie-info-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  flex: 3;
}

.movie-info-container div,
h3 {
  margin: 5px;
}

.movie-info-comment {
  display: flex;
  justify-content: center;
}

.rating {
  color: gold;
  font-size: 4rem;
  padding: 20px;
}

.rating-bar {
  padding: 20px 10px;
}

.far {
  margin-right: 5px;
}
</style>
