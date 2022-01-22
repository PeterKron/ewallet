<template>
  <main>
      <h1>ADD A NEW CARD</h1>
      <section :class="CardColor">

        <img src="../assets/wifi.svg" alt="">
        <img src="../assets/chip.svg" alt="">

        <img class="vendor-img" :src="currentUrl" alt="">

        <h2>{{Card.Cardnumber}}</h2>


            <p class="smallerp">CARDHOLDER NAME</p>
            <p>{{Card.Cardholder}}</p>

            <p class="smallerp">VALID THRU</p>
            <p>{{Card.Month}}</p><p>{{Card.Year}}</p>
        
      </section>
      <CardForm
      @RenderCard="RenderCard"
      @ChangePage="$emit('ChangePage')"
      @AddtoList="(payload) => $emit('AddtoList', payload)"
      />
      <!-- @AddtoList="AddtoList" -->
  </main>
</template>

<script>
import CardForm from './CardForm.vue'


export default {

    components: {CardForm},
    data(){return{
        currentUrl: require("../assets/bitcoin-grey.svg"),
        Card: {},
        CardColor: "",
    }},
    methods: {
        RenderCard(Card){
        this.Card = Card
        this.currentUrl = require("../assets/"+ Card.Vendor +".svg")
        this.CardColor = Card.Vendor
        }
    }
}
</script>

<style lang="scss" scoped>

section {
    width: 366px;
    height: 224px;
    // width: 382px;
    // height: 240px;
    padding: 16px 16px 16px 16px;
    
    border-radius: 8px;
    background: linear-gradient(248.3deg, rgba(255, 255, 255, 0.24) 0%, rgba(255, 255, 255, 0) 100%),
    #D0D0D0;
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.08); 
    display:grid;
}


.smallerp {
    font-size: 12px;
}
.Evil{
    background: linear-gradient(248.3deg, rgba(0, 0, 0, 0.16) 0%, rgba(0, 0, 0, 0) 100%),
    #F33355;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
    p, h2 {
    color: white;
    }
}
.Bitcoin{
    background: linear-gradient(248.04deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 99.07%),
    #FFAE34;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
}
.Ninja {
    background: linear-gradient(248.3deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 100%),
     #222222;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
    p, h2 {
    color: white;
    }
}
.Blockchain {
    background: linear-gradient(248.52deg, rgba(0, 0, 0, 0.15) 1.49%, rgba(0, 0, 0, 0) 100%),
    #8B58F9;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
    p, h2 {
    color: white;
    }
}
</style>
