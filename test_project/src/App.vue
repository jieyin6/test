<template>
  <div id="app">
    <input-number v-model="value" :max="10" :min="0"></input-number>
    <router-view/>
  </div>
</template>

<script>
import a from "./components/input-number"
export default {
  name: 'App',
  components:{
    "input-number":a
  },
  data:function(){
    return {
      value:5
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
