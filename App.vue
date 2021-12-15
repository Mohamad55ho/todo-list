<template>
  <div id="app">
<HelloWorld></HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    // eslint-disable-next-line vue/no-unused-components
    HelloWorld
  }
}
</script>

<style>
body{
  background-image: url(https://images.pexels.com/photos/5905452/pexels-photo-5905452.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940);
}
table{
  background-color: white;
}
/*#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}*/
</style>
