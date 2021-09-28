<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div v-for="mailRandomica in 10" :key="10">
      {{ mailRandomica }}
    </div>
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
     mailRandomica : 0
    }
  },
  mounted(){
    console.log(axios);
    axios.get('https://flynn.boolean.careers/exercises/api/random/mail')
    .then((response)=> {
      const result = response.data;
      console.log(result.response);
      this.mailRandomica = result.data.response;
    })
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
