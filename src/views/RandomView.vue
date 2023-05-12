
<template>
  <div>
    <h2>Random Movie</h2>
    <div v-if="weather">
      <h3>날씨: {{ weather }}</h3>
    </div>

    <button @click="getRandomMovie">랜덤</button>
    <div v-if="randomMovie">
      <h3>{{ randomMovie.title }}</h3>
      <img
        :src="'https://image.tmdb.org/t/p/w200/' + randomMovie.poster_path"
        :alt="randomMovie.title"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "MovieView",
  data() {
    return {
      movies: [],
      randomMovie: null,
      weather: null,
    };
  },
  created() {
    axios
      .get("https://api.themoviedb.org/3/movie/top_rated?language=ko-KR", {
        params: {
          api_key: "6e4f60ea88e44702b1782875498a4af2", // The Movie Database API 키로 대체해야 합니다.
        },
      })
      .then((response) => {
        this.movies = response.data.results;
        this.randomMovie = this.movies[0];
      })
      .catch((error) => {
        console.log(error);
      });
    this.getWeather();
  },
  methods: {
    getRandomMovie() {
      const randomIndex = Math.floor(Math.random() * this.movies.length);
      this.randomMovie = this.movies[randomIndex];
    },
    getWeather() {
      axios
        .get("https://api.openweathermap.org/data/2.5/weather?q=Seoul,kor", {
          params: {
            APPID: "bf43c0b6dd7428e9ad104aed9e61da4d", // OpenWeatherMap API 키로 대체해야 합니다.
          },
        })
        .then((response) => {
          this.weather = response.data.weather[0].main;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>
