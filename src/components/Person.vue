<template>
<div>
  <h2>Rahidul Islam</h2>
  <h3>Counter {{ counter}} </h3>
  <button v-on:click="increase(1)">Increase 1</button>
  <button v-on:click="decrease(1)">Decrease 1</button>
  <button v-on:click="increase(2)">Increase 2</button>
  <button v-on:click="decrease(2)">Decrease 2</button>
  <button v-on:click="test">Test</button>
</div>
</template>

<script>
export default{
  name: "Person",
  data(){
    return {
      counter: 0
    }
  },

  methods: {
    increase(count){
      this.counter += count
    },
    decrease(count){
      this.counter -= count
    },
    test(e){
      console.log("test")
      console.log(e)
    }
  }
}
</script>

<style>

</style>