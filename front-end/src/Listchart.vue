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
                // labels:
                datasets: [{
                    backgroundColor: '#f87979',
                    data: [10, 10, 10 , 10, 10, 10 , 10, 10, 10, 10],
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
                
               let array1 = [];

               // инициализация массива
               for (let index = 0; index < 100; index++) {
                   array1.push([this.postchart[index].userId,this.postchart[index].title]);
               } 

                 for (let ik = 0; ik < array1.length; ik++) {
                    let name_unique = array1[ik][0];
                    for (let j = 0; j <array1.length; j++) {
                        let name_not_unique =array1[j][0];
                    if(ik != j  && name_unique == name_not_unique){
                        array1.splice(ik, 1);
                        ik-=1;
                        break;
                    }
                }
            }

            let obj = [];
            // label: [1, 2, 3,]
            for (var i = 0; i < array1.length; i++) {
                obj.push(array1[i][0]);
            }
            return obj;

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