<template>
  <div id="app">
    <Home 
    v-if="currentView == 'home'"
    :CardListData="cardlistdata"
    />

    <AddNewCard 
    v-else-if="currentView == 'addnewcard'"
    @ChangePage="ChangePage"
    @AddtoList="AddtoList"
    />
    <!-- lyssnare som byter värde på currentView -->

    <nav>
      <!-- <a v-if="currentView == 'addnewcard'" @click="currentView = 'home'">ADD CARD</a> -->
      <button v-if="currentView == 'home'"
      @click="currentView = 'addnewcard'">
      ADD A NEW CARD
      </button>
    </nav>
  </div>
</template>

<script>
  import Home from './views/Home.vue'
  import AddNewCard from './views/AddNewCard.vue'

export default {
  components: {Home, AddNewCard,},
  methods: {
    ChangePage(Page){
      this.currentView = Page
    },
    AddtoList(Card){
      this.cardlistdata.push(Card)
    }
  },
  data(){return{
    currentView: "home",
    cardlistdata: [
      // { 
      //   cardNumber:"1234 5678 1910 1112",
      //   cardholder:"Fredrik Fredriksson",
      //   expireMonth:"11",
      //   expireYear:"22",
      //   CCV:"312",
      //   vendor: "bit",
      // }
    ],
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
a {
  font-size: 1rem;
  border: 5px solid;
  border-radius: 5%;
}
nav {
  margin: 5rem;
}
</style>
