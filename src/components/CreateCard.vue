<template>
  <main>
      <h1>ADD A NEW BANK CARD</h1>
      <CardItem 
      :Card="Card"
      />
      <CardForm
      @RenderCard="RenderCard"
      @ChangePage="$emit('ChangePage')"
      @AddtoList="(payload) => $emit('AddtoList', payload)"
      :CardListData="CardListData"
      />
  </main>
</template>

<script>
import CardItem from '../components/CardItem.vue'
import CardForm from './CardForm.vue'

export default {
    props: ['CardListData'],
    components: {CardForm, CardItem},
    data(){return{
        currentUrl: "",
        Card: {},
        CardColor: "",
        wifi: require("../assets/wifi.svg"),
    }},
    methods: {
        RenderCard(Card){
        this.Card = Card
        this.CardColor = Card.Vendor
        // this.currentUrl = require("../assets/"+ Card.Vendor +".svg")
        if(Card.Vendor == ""){this.currentUrl = ""}else {this.currentUrl = require("../assets/"+ Card.Vendor +".svg")}
        if(Card.Vendor == "Evil" || Card.Vendor == "Ninja"|| Card.Vendor =="Blockchain"){
            this.wifi = require("../assets/wifi_white.svg")
        }else {
            this.wifi = require("../assets/wifi.svg")
            }
        }
    }
}
</script>

<style lang="scss">

</style>
