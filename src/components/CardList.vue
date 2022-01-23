<template>
      <ul>
        <CardItem 
        v-for="Card in Card" :key="Card.Cardnumber"
        :Card="Card"
        />
        <!-- <h1 v-if="Card == Array">you need to add cards, to do it press button below</h1> -->
      </ul>
</template>

<script>

import CardItem from '../components/CardItem.vue'
export default {
  components: {CardItem},
  props: ['Card'],
  // data (){return{
  //   currentUrl: "",
  //   CardColor: "",
  //   wifi: require("../assets/wifi.svg"),
  // }},
  // beforeUpdate: function (){
  //   this.displaylogo()
  // },
  // methods:{
  //   displaylogo (){
  //       if(this.Card.Vendor == ""){this.currentUrl = ""}else {this.currentUrl = require("../assets/"+ this.Card.Vendor +".svg")}
  //       if(this.Card.Vendor == "Evil" || this.Card.Vendor == "Ninja"|| this.Card.Vendor =="Blockchain"){
  //       this.wifi = require("../assets/wifi_white.svg")
  //       }else {
  //       this.wifi = require("../assets/wifi.svg")
  //       }
  //   }
  // }
}
</script>

<style>
ul {
    padding: 0;
    /* margin: 0; */
}
</style>

