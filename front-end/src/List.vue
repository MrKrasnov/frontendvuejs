<template>
<div id="list">
  <div class="container">
    <div class="post">
        <div class="info">
         {{post.id}}
        </div>
        <div>
          <p><span>Name:</span> {{post.name}}</p>
           <p><span>Username:</span> {{post.username}}</p>
           <p><span>Email:</span> {{post.email}}</p>
         </div>
          <div>
         <ul><span>Adress:</span>
           <li><span>Street:</span> {{post.address.street}}</li>
           <li><span>Suite:</span> {{post.address.suite}}</li>
            <li><span>City:</span> {{post.address.city}}</li>
           <li><span>Zipcode:</span> {{post.address.zipcode}}</li>
           <li><span>Geo:</span>
                <p><span>lat:</span> {{post.address.geo.lat}}</p>
                <p><span>lng:</span> {{post.address.geo.lng}}</p>
          </li>
         </ul>
          </div>
         <div>
          <p><span>Phone:</span> {{post.phone}}</p>
          <p><span>Website:</span> {{post.website}}</p>
          </div>
         <div>
          <ul> <span>Company:</span>
           <li><span>Name:</span>"{{post.company.name}}"</li>
            <li><span>Motto:</span> {{post.company.catchPhrase}}</li>
            <li><span>Product:</span> {{post.company.bs}}</li>
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
span{
  font-weight: bold;
}
</style>