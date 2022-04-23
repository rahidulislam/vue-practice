<template>
  <h3>Part 13</h3>
  <table border="1">
      <tbody>
          <tr v-for="(value, key, i) in aboutMe" :key="key">
              <th>{{ i }}</th>
              <th>{{ key }}</th>
              <td>{{ value }}</td>
          </tr>
      </tbody>
  </table>
  <p>
      <template v-for="skill in skills">{{ skill}}, </template>
  </p>
</template>

<script>
export default {
    name:"Part13",
    data(){
        return {
            aboutMe:{
                name: "Rahidul Islam",
                nickName: "Rubel",
                website: "https://google.com"
            },
            skills: ["HTML", "CSS", "Javascript"]
        }
    },
    methods:{

    }
}
</script>

<style>

</style>