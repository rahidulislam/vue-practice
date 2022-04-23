<template>
  <div>
      <h3>Event Handling</h3>
      <form @submit.prevent="handleSubmit">
        <input type="text" @keyup.enter="handleKeyUp">
        <p>Welcome {{ name }}</p>
        <button type="submit">Ok</button>
        
        <div class="card" @click="handleClick">
            <button @click.stop="handleViewClick">View</button>
        </div>
      </form>
      

  </div>
</template>

<script>
export default {
    name:'Part7',
    data(){
        return {
            name: ''
        }
    },
    methods:{
        handleKeyUp(e){
            console.log(e.target.value)
            this.name = e.target.value
        },
        handleSubmit(e){
            console.log(e)
        },
        handleClick(){
            console.log("Card Clicked")
        },
        handleViewClick(e){
            console.log("View Clicked")
        }
    }
}
</script>

<style>
.card{
    width: 200px;
    height: 200px;
    border: 1px solid green;
    margin-top: 50px;
}
</style>