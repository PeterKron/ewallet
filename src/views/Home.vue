<template>
  <main class="Home">
    <h1>WELCOME TO E-WALLET</h1>
    <div v-if="!(Card == '')">
      <CardItem :Card="kort" 
      @click="flipcard"
      />
    </div>

    <CardList
    :Card="Card"
    @ActiveCard="RenderCard"
    />
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
import CardList from '../components/CardList.vue'
import CardItem from '../components/CardItem.vue'
export default {
  components: {CardList, CardItem},
  props: ['Card'],
  data(){return{
    kort: {},
  }},
  methods: {
    flipcard(){
      alert('notabletoflipcardjustyet')
    },
    RenderCard(Card){
        this.kort = Card
    }
  },
}
</script>

<style lang="scss" scoped>

</style>