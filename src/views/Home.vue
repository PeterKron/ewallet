<template>
<!-- :class="{remove}" -->
  <main class="Home" >
    <h1 :class="{remove}">WELCOME TO E-WALLET</h1>
    <section v-if="Card.length > 0">
      <CardItem :Card="kort" :class="{remove}"/>
      <!-- @ActiveCard="flipcard" -->
      <button @click="remove = true" :class="{remove}">REMOVE CARD</button>
      <div class="remove-box" v-if="remove == true">
        <p>Are you sure you would like to remove this card?</p>
        <div>
        <button @click="removeCard">Yes</button>
        <button @click="remove = false">No</button>
        </div>
      </div>
    </section>

    <ul :class="{remove}">
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
    <button :class="{remove}" @click="$emit('ChangePage', 'addnewcard')"> ADD A NEW CARD</button>
  </main>
</template>

<script>
import CardItem from '../components/CardItem.vue'
export default {
  components: {CardItem},
  props: ['Card'],
  data(){return{
    kort: this.Card[this.Card.length -1],
    remove: false
  }},
  methods: {
    renderCard(Card){
      this.kort = Card
    },
    removeCard(){
      this.remove = false
      this.$emit('removeCard', this.kort)
      this.kort = this.Card[this.Card.length-1]
    }
      // flipcard(){
      //   console.log('notabletoflipcardjustyet')
      // },
  },
}
</script>

<style lang="scss" scoped>
.remove-box{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  background: black;
  color: white;
  border-radius: 10px;
  position: absolute;
  top: 100px;
  width: 350px;
  height: 100px;
  button {
    width: 50px;
    margin: 5px;
  }
}
.remove {
  -webkit-filter: blur(3px);
  -moz-filter: blur(3px);
  -o-filter: blur(3px);
  -ms-filter: blur(3px);
  filter: blur(3px);
}
main section:first-of-type {
  display: flex;
  flex-direction: column;
  align-items: center;
  
}
section button {
  padding: 5px;
  border-radius: 5px;
  border-width: 1px;
  font-size: 16px;
  margin-top: 5px;
  background-color: white;
  font-weight: bold;
}
section button:hover{
    background-color: rgb(173, 22, 22);
    color: white;
}
ul {
  display: grid;
  grid-auto-rows: 50px;
  padding: 0;
  margin: 8rem 0 6rem 0; 
}
</style>