<template>
  <header>
    <h1><router-link to="/">{{ title }}</router-link></h1>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    title: String
  },
  data() {
    return {
      name: 'Movie DB',
      show: false
    }
  }
}
</script>

<style scoped>
header {
  background-color: #111;
  height: 5vh;
  padding: 20px;
  color: white;
}
h1 {
  margin: 0;
}
a {
  color: #fff;
  text-decoration: none;
}
</style>
