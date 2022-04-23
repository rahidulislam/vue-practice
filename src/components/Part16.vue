<template>
  <h3>Part-16 Watcher</h3>
  <input type="text" v-model="mobile">
  <input type="text" v-model="name.firstName">
</template>

<script>
export default {
    name: "Part16",
    data(){
        return {
            mobile: "",
            name: {
                firstName: "",
            }
        }
    },
    computed:{

    },
    watch:{
        mobile(newValue, oldValue){
            console.log(newValue);
            if (isNaN(newValue)){
                alert("Enter valid Number");
                this.mobile=oldValue;
            }
            if(this.mobile.length == 11){
                alert("OTP Send")
            }
        },
        // 'name.firstName': function(newValue){
        //     console.log(newValue)
        // },
        name:{
            deep: true,
            handler: function(newValue){
                console.log(newValue)
            }
        }
        
    },
    methods:{

    }
}
</script>

<style>

</style>