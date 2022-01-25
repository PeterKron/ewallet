<template>
  <main>
      <section :class="Card.Vendor" @click="$emit('ActiveCard')">
          <div class="chipbox">
            <img :src="wifiPath" alt="">
            <img src="../assets/chip.svg" alt="">
          </div>
        <div class="logo">
        <img class="vendor-img" :src="logoPath" alt="">
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
  </main>
</template>

<script>
export default {
    props: ['Card'],
    computed: {
        logoPath(){
            if(this.Card.Vendor == "") {return "original"}
            else {return require("../assets/"+ this.Card.Vendor +".svg")}
        },
        wifiPath () {
            if(this.Card.Vendor == "Evil" || this.Card.Vendor == "Ninja"|| this.Card.Vendor =="Blockchain")
            {return require("../assets/wifi_white.svg")}
            return require("../assets/wifi.svg")
        },
    },    
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
        p:last-of-type { text-transform: uppercase;}
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
.original {
    background: linear-gradient(248.3deg, rgba(255, 255, 255, 0.24) 0%, rgba(255, 255, 255, 0) 100%),
    #D0D0D0;
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.08); 
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
