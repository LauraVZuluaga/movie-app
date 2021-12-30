<template>
  <Loading v-if="$fetchState.pending" />
  <div v-else class="container single movie">
    <NuxtLink class="button" :to="{ name: 'index' }"> Back </NuxtLink>
    <div class="movie-info">
      <div class="movie-img">
        <img
          :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`"
          alt=""
        />
      </div>
      <div class="movie-content">
        
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'single-movie',
  data() {
    return {
      movie: '',
    }
  },

  async fetch() {
    await this.getSingleMovie()
  },

  fetchDelay: 1000,

  methods: {
    async getSingleMovie() {
      const data = axios.get(
        `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=8887f834cb749f1169b42bc18530f525&language=en-US `
      )

      const result = await data
      this.movie = result.data
    },
  },
}
</script>
<style lang="scss" scoped></style>
