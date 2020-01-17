<template>
  <div id="app">
    <list v-for="post in posts"
          :key="post.id"
          :name="post.name"
          :username="post.username"
      ></list>
  </div>
</template>

<script>
import List from './List.vue'

export default {
  components: {
    List
  },
  name: 'app',

  data() {
    return {
      posts: [],
      userFilter: this.posts
    }
  },
  
 

  // получаю данные
  created: function () {

    let vm = this;
    
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(function (response) {
        return response.json()
      })
      .then(function (data) {
        vm.posts = data
      })
  },

}
</script>

<style>
body{
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.post li p {
  border: none;
}
p{
  margin: 0;
}
.post{
  padding-top: 20px;
  display: flex;
  justify-content: space-between;
  color:#2c3e50;
  font-size: 15px;
}
.info{
  padding-left: 20px;
}
ul{
  margin: 0;
}
</style>
