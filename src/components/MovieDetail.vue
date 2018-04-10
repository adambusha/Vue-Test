<template>
<transition name="fade">
  <div class="movie-wrapper" :style="styles">
    <div class="movie-info">
      <h1>{{ movie.title }}</h1>
      <h3>Release Date: {{ movie.release_date }}</h3>
      <p>{{ movie.overview }}</p>
      <p>Average Rating: {{ movie.vote_average }}/10 ({{ movie.vote_count }} votes)</p>
    </div>
  </div>
</transition>
</template>

<script>
const BACKDROP_PATH = 'https://image.tmdb.org/t/p/w1280'
export default {
  name: "MovieDetail.vue",
  data () {
    return {
      movie: {}
    }
  },
  created: function () {
    this.fetchData()
  },
  computed: {
    styles () {
      return {
        'background-image': `url(${BACKDROP_PATH}/${this.movie.backdrop_path})`
      }
    }
  },
  methods: {
    fetchData: async function () {
      try {
        const res = await fetch(
          `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=4f485c5af1cd144d48927a9cbfe45038`
        )
        const movie = await res.json()
        this.movie = movie
      } catch (e) {
        console.log(e)
      }
    }
  }
}
</script>

<style scoped>
.movie-wrapper {
  background-repeat: no-repeat;
  background-size: cover;
  height: 30vh;
  padding-top: 60vh;
  position: relative;
}
.movie-info {
  background: rgba(255,255,255,.9);
  color: #222;
  height: 25vh;
  padding: 2rem 10%;
}
</style>
