<template>
  <div id="app">
    <RecordsContainer/>
  </div>
</template>

<script>
import RecordsContainer from './components/RecordsContainer.vue'

export default {
  name: 'App',
  components: {
    RecordsContainer
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #2e3a46;
  height: 100vh;
}
</style>
