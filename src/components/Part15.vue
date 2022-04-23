<template>
  <h3>Part 15</h3>
  <ul>
      <li v-for="skill in skills" :key="skill.id">
          {{ skill.name }}({{ skill.experience }})
      </li>
  </ul>
  <h3>Total Skill {{ totalSkill }}</h3>
  <h4>Top Skill</h4>
  <ul>
      <li v-for="skill in topSkills" :key="skill.id">
          {{ skill.name }}({{ skill.experience }})
      </li>
  </ul>
  
</template>

<script>
export default {
    name: "Part15",
    data(){
        return {
            skills:[
                {
                    id: 1,
                    name: "HTML",
                    experience: 10
                },
                {
                    id: 2,
                    name: "CSS",
                    experience: 15
                },
                {
                    id: 3,
                    name: "JavaScript",
                    experience: 5,
                },
                {
                    id: 4,
                    name: "Python",
                    experience: 6
                },
                {
                    id: 5,
                    name: "DJango",
                    experience: 10
                },
            ]
        }
    },
    computed:{
        totalSkill(){
            console.log(this.skills.length)
            return this.skills.length
        },
        topSkills(){
            let es = this.skills.filter(item=>{
                return item.experience>=10
            });
            return es;
        }
    }
}
</script>

<style>

</style>