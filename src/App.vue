<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to our first mail list getter"/>
    <div v-for="mail in listaMail" :key="mail">{{ mail }}</div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from "axios"
export default {

  name: 'App',
  components: {
    HelloWorld
  },
  data: function (){
    return{
    listaMail:[],
    }
  },
  mounted(){
    for ( let i = 0; i < 10; i ++ ) {
    console.log(axios);
    axios.get('https://flynn.boolean.careers/exercises/api/random/mail')
    .then((response)=> {
      const result = response.data;
      console.log(result.response);
      this.listaMail.push(result.response);
    })
    }
    console.log(this.listaMail)
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
