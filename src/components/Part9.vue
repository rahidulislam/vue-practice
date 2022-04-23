<template>
    <h3>class binding</h3>
  <button :class="{active: activeClass == 'red'}" @click="setClass('red')">Red</button>
  <button :class="{active: activeClass == 'green'}" @click="setClass('green')">Green</button>
  <button :class="{active: activeClass == 'blue'}" @click="setClass('blue')">Blue</button>
  <div :class="activeClass"></div>
</template>

<script>
export default {
    name: 'Part9',
    data(){
        return {
            activeClass: 'red'
        }
    },
    methods:{
        setClass(className){
            this.activeClass = className
        }
    }
}
</script>

<style>
.active{
    background-color: orangered;
}
.red{
    width: 100px;
    height: 50px;
    background-color: red;
}
.green{
    width: 100px;
    height: 50px;
    background-color: green;
}
.blue{
    width: 100px;
    height: 50px;
    background-color: blue;
}
</style>