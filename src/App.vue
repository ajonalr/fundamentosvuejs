<template>
  <!-- <Counter title="Entraron" :star="10"/> -->
  <indesision />
  
  <!-- <Counter /> -->
</template>

<script>
import Counter from "./components/Counter";
import Indesision from './components/Indesision.vue';
export default {
  name: 'App',
  components: {
    Counter,
    Indesision
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
