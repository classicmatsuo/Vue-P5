<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <Osc msg="Osc staging"/>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Test/> -->
    <!-- <Test2/> -->
    <Test3/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import Osc from './components/Osc.vue'
// import Test from './components/Test.vue'
// import Test2 from './components/Test2.vue'
import Test3 from './components/Test3.vue'

export default {
  name: 'app',
  components: {
    // HelloWorld,
    // Osc,
    // Test,
    // Test2,
    Test3
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
