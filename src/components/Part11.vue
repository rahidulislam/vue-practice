<template>
  <h3>List Rendering</h3>
  <input type="text" v-model="newSkill">
  <button @click="addSkill">Add</button>
  <ul>
      <li v-for="(skill,i) in skills" :key="i" @click="removeSkill(i)">
          {{ i+1 }} {{ skill }}
      </li>
    </ul>
</template>

<script>
export default {
    name: 'Part11',
    data(){
        return {
            skills: ["HTML", "CSS", "Javascript"],
            newSkill: ""
        }
    },
    methods: {
        addSkill(){
            this.skills.push(this.newSkill);
            this.newSkill=""
        },
        removeSkill(i){
            this.skills.splice(i,1)
        }
    }
}
</script>

<style>

</style>