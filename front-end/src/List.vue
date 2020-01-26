<template>
<div id="list">
  <div class="container">
    <div class="post">
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
    </div>

</template>
     
    

<script>
    export default {
        props: ['post'],
        name: 'list',
        data: function () {
            return {
            selected: ''
            }
        },
    }
</script>

<style scoped>
.container {
  padding-top: 20px;
  width: 85%;
  margin: 0 auto;
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
  border: 1px solid black;
  padding-bottom: 10px;
  
}
.info{
  padding-left: 20px;
}
ul{
  margin: 0;
  font-weight: bold;
}
ul li{
  font-weight: 400;
  display: block;
}
</style>