<template>
  <div id="app">

    <select v-model="selected">
      <option disabled value="">Выберите имя</option> 
      
        <option v-for="post in posts" :key="post.id">
          {{post.name}}
        </option>
        
    </select>
      
        <list v-for="post in filterList"
          :key="post.id"
          :post="post"
        ></list>
      
    <listchart>
    </listchart>
    
  </div>

</template>

<script>
import List from './List.vue'
import Listchart from './Listchart.vue'


export default {
  components: {
    List,
    Listchart,
  },
  name: 'app',

  data() {
    return {
      posts: [],
      userFilter: this.posts,
      selected: '',
      
    }
  },
  
  //фильтр
  computed: {
    filterList: function (){
      let sel = this.selected;
      return this.posts.filter(function (elem) {
        if(sel === '') return true;
        else return elem.name.indexOf(sel) > -1;
      }) 
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
  padding-top: 15px;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
select{
  display: block;
  border-radius: 5px;
  height: 30px;
  margin: 0 auto;
}
select:hover{
  outline: none;
}
select:focus{
  outline: none;
}
</style>
