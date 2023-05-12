<template>
  <div>
    <h2>Random Movie</h2>
    <div v-if="weather">
      <h3>오늘의 날씨 {{ weather }}에 맞는 영화 추천</h3>
    </div>

    <button @click="getRandomMovie">랜덤</button>
<div v-if="randomMovie">
  <h3>{{ randomMovie.genres_name }}</h3>
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
          api_key: "6e4f60ea88e44702b1782875498a4af2", 
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
            APPID: "bf43c0b6dd7428e9ad104aed9e61da4d",
          },
        })
        .then((response) => {
          const weather = response.data.weather[0].main;
          this.recommendMovieBasedOnWeather(weather);
          this.weather = weather;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    recommendMovieBasedOnWeather(weather) {
      if (weather === "Clear") {
        this.randomMovie = this.movies.find(
          (movie) => movie.genre_ids.includes(80) //드라마
        );
      
      } else if (weather === "Clouds") {
        this.randomMovie = this.movies.find(
          (movie) =>movie.genre_ids.includes(18) //범죄
        );

      } else {
        this.randomMovie = this.movies.find(
          (movie) => movie.genre_ids.includes(14) //판타지
        );
      }
    },
  },
};
</script>
<style>
</style>
