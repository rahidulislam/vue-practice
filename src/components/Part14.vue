<template>
<h3>Part 14 V-IF</h3>
<button @click="toggleShow">Show/Hide</button>
  <div class="card" v-if="show"></div>
  
</template>

<script>
export default {
    name: "Part14",
    data(){
        return{
            show: false
        }
    },
    methods:{
        toggleShow(){
            this.show =! this.show;
        }
    }
}
</script>

<style>
    .card{
        width: 200px;
        height: 200px;
        border: 1px solid red;
    }
</style>