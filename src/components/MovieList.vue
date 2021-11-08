<template>
  <div class="list-item-container">
    <div class="img-container">
      <img :src="movie.poster ? movie.poster : image" :alt="movie.name" />
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
        <div><i class="far fa-heart"></i><span class="text">{{ movie.likeCount }}</span></div>
        <div><i class="far fa-comment-alt"></i><span class="text">{{ movie.reviewCount }}</span></div>
      </div>
      <div>{{ formatDate(new Date(movie.openDate)) }}</div>
    </div>
  </div>
</template>

<script>
import StarRating from "vue-star-rating";
import image from "../assets/no-poster-available.png";

export default {
  name: "MovieList",
  props: {
    movie: Object,
  },
  components: { StarRating },
  data() {
    return { image: image };
  },
  methods: {
    formatDate(date) {
    var d = new Date(date),
        month = '' + (d.getMonth() + 1),
        day = '' + d.getDate(),
        year = d.getFullYear();

    if (month.length < 2) 
        month = '0' + month;
    if (day.length < 2) 
        day = '0' + day;
    return [year + "年", month + "月", day + "日"].join('');
}
  }
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

.img-container {
  flex: 1;
}

.movie-rating-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex: 1;
  border-bottom: gray 1.5px solid;
}

.movie-info-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  flex: 3;
  border-bottom: gray 1.5px solid;
}

.movie-info-container div,h2 {
  margin: 5px;
}

.movie-info-comment {
  display: flex;
  justify-content: center;
}

.rating {
  color: gold;
  font-size: 4rem;
  font-weight: 700;
  padding: 0 20px;
}

.rating-bar {
  padding: 0 10px;
}

.far {
  margin-right: 5px;
}

.text {
  color: gold;
  margin-right: 10px;
}
</style>
