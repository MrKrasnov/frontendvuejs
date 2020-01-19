<template>
 <chartjs-doughnut
    v-bind:labels="labels"
    v-bind:datasets="datasets"
    v-bind:option="option"
 ></chartjs-doughnut>
</template>

<script>
    
    export default {
        
        props: ['postes'],
        name: 'listchart',

        data (){
            return {
                labels: ['apple' , 'banana', 'Grapes'],
                datasets: [{
                    data: [20, 30, 50 ],
                    backgroundColor: ['Red', 'Yellow', 'Purple']
                }],
                option: {
                    title: {
                        display: true,
                        position: 'bottom',
                        text: "Fruits"
                    }
                }

            };
        }
    }
</script>

<style>
</style>