<template>
  <div>
    <h2>Random Movie</h2>
    <button @click="getRandomMovie">랜덤</button>
    <div v-if="randomMovie">
      <h3>{{ randomMovie.title }}</h3>
      <img :src="'https://image.tmdb.org/t/p/w200/' + randomMovie.poster_path" :alt="randomMovie.title">
    </div>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  name: 'MovieView',
  data() {
    return {
      movies: [],
      randomMovie: null
    }
  },
  created() {
    axios.get('https://api.themoviedb.org/3/movie/top_rated?language=ko-KR', {
      params: {
        api_key: '6e4f60ea88e44702b1782875498a4af2'
      }
    })
      .then(response => {
        this.movies = response.data.results
        this.randomMovie = this.movies[0]
      })
      .catch(error => {
        console.log(error)
      })
  },
  methods: {
    getRandomMovie() {
      const randomIndex = Math.floor(Math.random() * this.movies.length)
      this.randomMovie = this.movies[randomIndex]
    }
  }
}
</script>
<style>

</style>