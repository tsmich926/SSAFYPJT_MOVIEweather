<template>
  <div>
    <h1>보고 싶은 영화 등록</h1>
    <form @submit.prevent="addMovie">
      <input type="text" v-model.trim="newMovie" placeholder="영화 제목">
      <button type="submit">등록</button>
    </form>
    <h1>보고 싶은 영화 목록</h1>
    <ul>
      <li v-for="(movie, index) in movies" :key="index" @click="toggleMovie(movie)">
        <span :class="{ 'completed': movie.completed }">{{ movie.title }}</span>
        <button @click.prevent="removeMovie(index)">삭제</button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'WatchList',
  data() {
    return {
      newMovie: '',
      movies: []
    }
  },
  created() {
    if (localStorage.getItem('movies')) {
      this.movies = JSON.parse(localStorage.getItem('movies'))
    }
  },
  methods: {
    addMovie() {
      if (this.newMovie.trim()) {
        this.movies.push({
          title: this.newMovie.trim(),
          completed: false
        })
        this.newMovie = ''
        localStorage.setItem('movies', JSON.stringify(this.movies))
      }
    },
    toggleMovie(movie) {
      movie.completed = !movie.completed
      localStorage.setItem('movies', JSON.stringify(this.movies))
    },
    removeMovie(index) {
      this.movies.splice(index, 1)
      localStorage.setItem('movies', JSON.stringify(this.movies))
    }
  }
}
</script>
<style>
.completed {
  text-decoration: line-through;
}
</style>