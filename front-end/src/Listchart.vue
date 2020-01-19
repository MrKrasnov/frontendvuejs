<template>
 <chartjs-doughnut
    v-bind:labels="labels"
    v-bind:datasets="datasets"
    v-bind:option="option"
 ></chartjs-doughnut>
</template>

<script>
    
    export default {
        
        
        name: 'listchart',

        data (){
            return {
                postchart: [],
                labels: ['apple' , 'banana', 'Grapes'],
                datasets: [{
                    data: [20, 30, 50 ],
                }],
                option: {
                    title: {
                        display: true,
                        position: 'bottom',
                        text: "Fruits"
                    }
                }

            };
        },
        created: function () {
            let vm = this;
             fetch('https://jsonplaceholder.typicode.com/users/1/posts')
             .then(function (response) {
             return response.json()
             })
            .then(function (data) {
              vm.postchart = data
      })
        }
    }


    // fetch('https://jsonplaceholder.typicode.com/users/1/posts')
    //   .then(function (response) {
    //     return response.json()
    //   })
    //   .then(function (data) {
    //     vm.postchart = data
    //   })
</script>

<style>
</style>