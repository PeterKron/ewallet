<template>
  <div id="app">
    <nav>
      <a @click="currentView = 'home'">Home</a>
      <a @click="currentView = 'addnewcard'">About</a>
    </nav>
    <Home v-if="currentView == 'home'"/>
    <AddNewCard v-else-if="currentView == 'addnewcard'"/>
  </div>
</template>

<script>
  import Home from './views/Home.vue'
  import AddNewCard from './views/AddNewCard.vue'


export default {
  components: {Home, About, AddNewCard},
  data(){return{
    currentView: "home"
  }},

  name: 'App',
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
