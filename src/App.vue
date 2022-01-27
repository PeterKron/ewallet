<template>
  <main>
    <Home 
    v-if="currentView == 'home'"
    :Card="cardlistdata"
    @ChangePage="ChangePage"
    @removeCard="removeCard"
    />

    <AddNewCard 
    v-else-if="currentView == 'addnewcard'"
    @ChangePage="ChangePage"
    @AddtoList="AddtoList"
    :CardListData="cardlistdata"
    />
  </main>
</template>

<script>
  import Home from './views/Home.vue'
  import AddNewCard from './views/AddNewCard.vue'

export default {
  components: {Home, AddNewCard,},
  beforeMount: function () {
    if(localStorage.cardlist){
      this.cardlistdata = JSON.parse(localStorage.getItem("cardlist"))
    }
  },
  methods: {
    ChangePage(Page){
      this.currentView = Page
    },
    AddtoList(Card){
      this.cardlistdata.push(Card)
      localStorage.setItem('cardlist', JSON.stringify(this.cardlistdata))

    },
    removeCard(card){
      this.cardlistdata.splice(this.cardlistdata.indexOf(card), 1)
      localStorage.setItem('cardlist', JSON.stringify(this.cardlistdata))
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
main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
// nav {
//   padding-top: 5rem;
// }
.test {
  width: 400px;
  text-align: center;
  color:rgb(245, 13, 13);
  text-shadow: rgba(148, 140, 140, 0.432) 0.5px 0.8px;
}
h1 {
  font-family: Source Sans Pro, sans-serif;
}
p, label{
font-family: PT MONO, monospace;
margin: 0;
}
button {
  font-family: PT MONO, monospace;
}
.number {
 font-size: 29px;
}
.smallerp, label  {
  font-size: 12px;
}

</style>
