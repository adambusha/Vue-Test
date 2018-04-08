<template>
  <ul>
    <li v-for="movie in movies">
      <Movie :movie="movie" />
    </li>
  </ul>
</template>

<script>
import Movie from './Movie.vue'
export default {
  name: 'MoviesList',
  data () {
    return {
      movies: []
    }
  },
  created: function () {
    this.fetchData()
  },
  methods: {
    fetchData: async function () {
      try {
        const res = await fetch(
          'https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=65e043c24785898be00b4abc12fcdaae'
        )
        const movies = await res.json()
        this.movies = movies.results
      } catch (e) {
        console.log(e)
      }
    }
  },
  components: {
    Movie
  }
}
</script>

<style scoped>
ul {
  display: grid;
  grid-row-gap: 1rem;
  grid-template-columns: repeat(6, 1fr);
  list-style: none;
  margin: 0;
  padding: 1rem;
}
</style>
