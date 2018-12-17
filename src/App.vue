<template>
  <div id="app">
    <RepoSearch :items="['Bitcoin', 'Ethereum', 'Dogecoin']"/>
  </div>
</template>

<script>
import RepoSearch from './components/RepoSearch.vue'

export default {
  name: 'app',
  components: {
    RepoSearch
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #3f3f3f;
  margin-top: 0px;
}
</style>
