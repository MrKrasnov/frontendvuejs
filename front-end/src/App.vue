<template>
  <div id="app">
    
  </div>
</template>

<script>

export default {
  name: 'app',

  data() {
    return {
      posts: []
    }
  },

  async mounted() {
    const res = await fetch(
      'https://jsonplaceholder.typicode.com/users'
      );
    const posts = await res.json();
    this.posts = posts;
  }
 
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
