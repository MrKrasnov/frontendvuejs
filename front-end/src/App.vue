<template>
  <div id="app">
    <div v-for="post in posts" :key="post.id" class="post">
      <div class="info">
      {{post.id}}
      </div>
      <div>
        <p>Name: {{post.name}}</p>
        <p>Username: {{post.username}}</p>
        <p>Email: {{post.email}}</p>
      </div>
      <div>
      <ul>Adress:
        <li>Street: {{post.address.street}}</li>
        <li>Suite: {{post.address.suite}}</li>
        <li>City: {{post.address.city}}</li>
        <li>Zipcode: {{post.address.zipcode}}</li>
        <li>Geo:
            <p>lat: {{post.address.geo.lat}}</p>
            <p>lng {{post.address.geo.lng}}</p>
        </li>
      </ul>
      </div>
      <div>
      <p>Phone: {{post.phone}}</p>
      <p>Website: {{post.website}}</p>
      </div>
      <div>
      <ul> Company:
        <li>Name: "{{post.company.name}}"</li>
        <li>Motto: {{post.company.catchPhrase}}</li>
        <li>Product: {{post.company.bs}}</li>
      </ul>
      </div>
    </div>
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
