<script setup lang="ts">
export default {
  data() {
          return {
            count: 10,
            counterTitle: 'Counter Standard',
            incrementAmount: 8,
            message: "Hello it works!",
            listOfNumbers: [1, 2, 3, 4, 5]
          }
        },
        computed: {
          displayTitle() {
            if (this.count > 20){
              return 'Counter Standard - Very Long'
            } else{
              return 'Counter Standard'
            }
          },
          optimizedIncrementAmount() {
            return this.displayTitle.length * this.incrementAmount
          }
        },
        methods: {
          incrementCount(){
            this.count += this.optimizedIncrementAmount
          },
          changeIncrementAmount(event){
            this.incrementAmount = Number(event.target.value)
          }
        },
        watch: {
          count(newValue){
            if (newValue > 20){
              this.counterTitle += ' Very Long';
            }
          },
        },
      };
</script>

<template>  
  <h1>{{ displayTitle }}</h1>
  <p>{{ count }}</p>
  <button v-on:click="incrementCount">Increment count</button>
  <h1>{{ incrementAmount }}</h1>
  <p>{{ optimizedIncrementAmount }}</p>
  <div>
    <label for="incrementAmount">Increment by: </label>
    <input type="number" 
    v-model.number="incrementAmount"
    /> 
  </div>
  <hr>

  <p v-if="message.length % 2 === 0"> Even: {{ message }} </p>
  <p v-else> Odd: {{ message }} </p>
  <ul>
    <li v-for="number in listOfNumbers">{{ number }}</li>
  </ul>
</template>

