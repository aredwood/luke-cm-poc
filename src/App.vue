<template>
  <div id="app">
    <ClassList/>
  </div>
</template>

<script>
import ClassList from "./components/ClassList";
export default {
  name: 'app',
  components: {
    ClassList
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
