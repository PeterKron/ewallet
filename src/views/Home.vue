<template>
  <main class="Home">
    <h1>WELCOME TO E-WALLET</h1>
    <div v-if="!(Card == '')">
      <CardItem :Card="kort" 
      @ActiveCard="flipcard"
      />
    </div>

    <ul>
    <CardItem 
    v-for="Card in Card" :key="Card.Cardnumber"
    :Card="Card"
    @ActiveCard="renderCard"
    />
    </ul>

    <h1 class="test" v-if="Card == ''">THERE IS NO CARDS.<br>PRESS BUTTON BELOW TO ADD CARD.</h1>
    <div>
    <img v-if="Card == ''" src="../assets/home-bitcoin.svg" alt="">
    <img v-if="Card == ''" src="../assets/home-ninja.svg" alt="">
    <img v-if="Card == ''" src="../assets/home-evil.svg" alt="">
    <img v-if="Card == ''" src="../assets/home-blockchain.svg" alt="">
    </div>
  </main>
</template>

<script>
import CardItem from '../components/CardItem.vue'
export default {
  components: {CardItem},
  props: ['Card'],
  data(){return{
    kort: {},
  }},
  methods: {
    flipcard(){
      console.log('notabletoflipcardjustyet')
    },
    renderCard(Card){
        this.kort = Card
    }
  },
}
</script>

<style lang="scss" scoped>
ul {
  display: grid;
  grid-auto-rows: 50px;
  padding: 0;
  margin: 8rem 0 6rem 0; 

}
</style>