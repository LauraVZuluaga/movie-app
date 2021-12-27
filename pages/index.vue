<template>
  <div class="home">
    <!--- Hero section---->
    <Hero />

    <!--- Movies section---->
    <div class="container movies">
      <div id="movie-grid">

      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  data() {
    return {
      movies: [],
    }
  },
  async fetch() {
    await this.getMovies()
  },
  methods: {
    async getMovies() {
      const data = axios.get(
        `https://api.themoviedb.org/3/movie/now_playing?api_key=8887f834cb749f1169b42bc18530f525&language=en-US&page=1`
      )
      const result = await data
      result.data.results.forEach((movie) => {
        this.movies.push(movie)
      })
      console.log(this.movies)
    },
  },
}
</script>
