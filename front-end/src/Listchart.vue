<template>
 <chartjs-doughnut
    v-bind:labels="labels"
    v-bind:datasets="datasets"
    v-bind:option="option"
    v-show="postchart.length > 0"
 ></chartjs-doughnut>
 
</template>

<script>
    
    export default {
        
        
        name: 'listchart',

        data (){ 
            return {
                postchart: [],
                
                datasets: [{
                    data: [20, 30, 50 ],
                }],
                option: {
                    title: {
                        display: true,
                        position: 'bottom',
                        text: "Message Users"
                    }
                }

            };
        },
        computed: {
            labels: function() { 
                
              return [this.postchart[1].userId, this.postchart[2].userId, this.postchart[3].userId];
            }
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
    
</script>

<style>
</style>