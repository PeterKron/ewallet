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
    cardlistdata: [],
  }},
  name: 'App',
}
</script>


<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro:wght@400;700&display=swap');
// * {
//   margin: 0;
// }

h1 {
  font-family: Source Sans Pro, sans-serif;
}
p, label{
font-family: PT MONO, monospace;
margin: 0;
}
.number {
 font-size: 29px;
}
.smallerp, label  {
  font-size: 12px;
}

</style>
