<template>
    <h3>Style binding</h3>
  <input type="text" v-model="bgColor">
  <input type="text" v-model="textColor">
  <input type="color" v-model="bgColor">
  <div :style="{backgroundColor: bgColor, color: textColor}">
    Card
  </div>
</template>

<script>
export default {
    name: 'Part10',
    data(){
        return {
            bgColor: 'red',
            textColor: 'green'
        }
    },
    methods: {

    }
}
</script>

<style>
    div{
        width: 100px;
        height: 100px;
    }
</style>