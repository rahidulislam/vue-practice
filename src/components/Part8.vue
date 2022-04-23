<template>
    <h3>Event and method binding</h3>
  <input v-model.number="num" type="text" >
  <br>
  <button @click="handleDouble">Get Double</button>
  <button @click="handleSquare">Get Square</button>
  <button @click="handleAddNumber">Add 10</button>
  <button @click="handleReset">Reset</button>
  <br>
  <label>Entered Number:{{ num }}</label>
  <br>
  <label>Result: {{ result }}</label>
</template>

<script>
export default {
    name: 'Part8',
    data(){
        return {
            num: '',
            result: ''
        }

    },
    methods:{
        handleDouble(){
            this.result = this.num * 2;
        },
        handleSquare(){
            this.result = this.num * this.num;
        },
        handleReset(){
            this.num = '';
            this.result = '';
        },
        handleAddNumber(){
            this.result = this.num + 10;
        }
        
    }
}
</script>

<style>

</style>