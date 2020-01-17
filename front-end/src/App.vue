<template>
  <div id="app">

    <select v-model="selected">
      <option disabled value="">Выберите один из вариантов</option> 
      
        <option v-for="post in posts" :key="post.id">
          {{post.id}}. {{post.name}}
        </option>
        
    </select>
    {{selected}}
      <template v-if="selected == ''">
        <list v-for="post in posts"
          :key="post.id"
          :post="post"
        ></list>
      </template>
      <template v-else>
        <list v-for="post in posts"
          :key="post.id"
          :post="post"
        ></list>
      </template>

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
      userFilter: this.posts,
      selected: ''
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
</style>
