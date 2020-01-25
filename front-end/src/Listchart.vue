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
                click: [],
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
                
               let localArray = [];

               // инициализация массива
               for (let index = 0; index < 100; index++) {
                   localArray.push([this.postchart[index].userId,this.postchart[index].title]);
               } 
                 for (let ik = 0; ik < localArray.length; ik++) {

                    let name_unique = localArray[ik][0];
                    for (let j = 0; j <localArray.length; j++) {
                        let name_not_unique =localArray[j][0];
                    // значение повторяется
                    if(ik != j  && name_unique == name_not_unique){
                        localArray.splice(ik, 1);
                        ik-=1;
                        break;
                    }
                }
            }

            let result = [];
            // label: [1, 2, 3,]
            for (var i = 0; i < localArray.length; i++) {
                result.push(localArray[i][0]);
            }
            return result;

            },
            datasets: function (){
                let array1 = [];

               // инициализация массива
               for (let index = 0; index < 100; index++) {
                   array1.push([this.postchart[index].userId,this.postchart[index].title]);
               } 
               let not_unique = [];
                // проверяем имя на повторность
                 for (let ik = 0; ik < array1.length; ik++) {
                     
                    let name_unique = array1[ik][0];
                    
                    for (let j = 0; j <array1.length; j++) {
                    // Берет такое же значение
                        let name_not_unique =array1[j][0];
                        
                    // если значение повторяется
                    if(ik != j  && name_unique == name_not_unique){
                        not_unique.push(array1[j][0]);
                        array1.splice(ik, 1);
                        ik-=1;
                        break;
                    }

                }
            }
            let result = [{
                    backgroundColor: '#f87979',
                    data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
                }];
                
                let data = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
                for(let user of not_unique){

                    switch(user){
                        case 1:
                            data[0] += 1;
                            break;
                        case 2:
                            data[1] += 1;
                            break;
                        case 3:
                            data[2] += 1;
                            break;
                        case 4:
                            data[3] += 1;
                            break;
                        case 5:
                            data[4] += 1;
                            break;
                        case 6:
                            data[5] += 1;
                            break;
                        case 7:
                            data[6] += 1;
                            break;
                        case 8:
                            data[7] += 1;
                            break;
                        case 9:
                            data[8] += 1;
                            break;
                        case 10:
                            data[9] += 1;
                            break;
                    }
                }
                const reducer = (accumulator, currentValue) => accumulator + currentValue;
                // один процент от общей суммы
                let OneInterest = data.reduce(reducer) / 100 * 1;
                //сохраняем проценты
                let resultInterest = [];
                
                for(let post of data){
                    // итерируем пока не получит цифру поста
                    let Interest = 0;
                    let WhileRes = 0
                    while(WhileRes != post){
                        Interest += 1;
                        // правильно добавляем дробные числа
                        WhileRes = (WhileRes * 10 + OneInterest * 10) / 10;
                    }
                    resultInterest.push(Interest);
                }
                result[0].data = resultInterest;
                return result;            
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