<template>
  <div>
    <h1>Register</h1>
    <input type= "text" 
    name= "email" 
    id= "email"
    v-model= "emailAddress">
    <input type= "password" 
    name= "password" 
    id= "password" 
    v-model= "pass"
    >
    <button @click="register">Register</button>
    <div id="resp"></div>
  </div>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService.js'
export default {
  name: 'HelloWorld',
  data () {
    return {
      emailAddress:"",
      pass:""
    }
  },
  methods:{
      async register(){
          const response = await AuthenticationService.register({
            email:this.emailAddress,
            pass: this.pass
        })
        console.log(`${response}`)
        document.getElementById('resp').innerHTML = JSON.stringify(response.data)
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
