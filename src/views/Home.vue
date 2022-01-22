<template>
  <main class="Home">
    <h1>ALL MY SEXY CARDSSS</h1>
      <p>HERE IS MY ACTIVE CARD btw in home</p>
      <section :class="CardColor">
          <div class="chipbox">
            <img :src="wifi" alt="">
            <img src="../assets/chip.svg" alt="">
          </div>
        <div class="logo">
        <img class="vendor-img" :src="currentUrl" alt="">
        </div>

        <p class="number">{{Card.Cardnumber}}</p>

        <div class="holderbox">
            <p class="smallerp">CARDHOLDER NAME</p>
            <p>{{Card.Cardholder}}</p>
        </div>

        <div class="validbox">
            <p class="smallerp">VALID THRU</p>
            <p>{{Card.Month}}/{{Card.Year}}</p>
        </div>
        
      </section>
        <p>HERE STARTS CARDLIST</p>
        <CardList
        :Card="Card"
        />
  </main>
</template>

<script>

import CardList from '../components/CardList.vue'
export default {
  components: {CardList},
  props: ['Card']
}
</script>


<style lang="scss" scoped>
main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
section {
    width: 382px;
    height: 240px;
    border-radius: 8px;
    background: linear-gradient(248.3deg, rgba(255, 255, 255, 0.24) 0%, rgba(255, 255, 255, 0) 100%),
    #D0D0D0;
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.08); 
    display:grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(3, 1fr);
    grid-template-areas: 
    "wifi . . logo"
    "cardn cardn cardn cardn"
    "cardh cardh cardh valid";
    .chipbox {
        grid-area: wifi;
        margin-top: 16px;
        img:first-of-type {
            margin: 0px 0px -8px 2px;
        }
    }
    .logo {
        display: flex;
        flex-direction: column;
        align-items: flex-end;
        grid-area: logo;
        margin: 16px 16px 0px 0px;
    }
    .number {
        grid-area: cardn;
        margin-top: 12px;
        letter-spacing: 0.03em;
    }
    .validbox, .holderbox {
        padding-top: 16px;
        display: flex;
        flex-direction: column;
    }
    .holderbox {
        grid-area: cardh;
    }
    .validbox {
        grid-area: valid;
        text-align: right;
        margin-right: 16px;
    }
    .chipbox, .holderbox, .number{
        margin-left: 16px;
    }
    .smallerp {
        margin-bottom: 5px;
    }
}
.Evil{
    background: linear-gradient(248.3deg, rgba(0, 0, 0, 0.16) 0%, rgba(0, 0, 0, 0) 100%),
    #F33355;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
    p, h2 {
    color: white;
    text-shadow:  -0.5px -0.5px rgba(0, 0, 0, 0.55);
    // text-shadow: 0.5px 0.5px 0px 0px rgba(0, 0, 0, 0.55) inset;
    }
}
.Bitcoin{
    background: linear-gradient(248.04deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 99.07%),
    #FFAE34;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
    p, h2 {
    text-shadow: -0.5px -0.5px rgba(254, 254, 254, 0.24);
    }
}
.Ninja {
    background: linear-gradient(248.3deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 100%),
     #222222;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
    p, h2 {
    color: white;
    text-shadow:  -0.5px -0.5px rgba(172, 172, 172, 0.25);
    }
}
.Blockchain {
    background: linear-gradient(248.52deg, rgba(0, 0, 0, 0.15) 1.49%, rgba(0, 0, 0, 0) 100%),
    #8B58F9;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
    p, h2 {
    color: white;
    text-shadow:  -0.5px -0.5px rgba(0, 0, 0, 0.55);
    }
}
</style>