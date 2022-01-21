<template>
  <div>
      <section>
        <img :src="currentUrl" alt="">
        <!-- <img src="../assets/ninja.svg" alt=""> -->
        <p>{{Card.Cardnumber}}</p>
        <p>{{Card.Cardholder}}</p>
        <p>{{Card.Month}}</p>
        <p>{{Card.Year}}</p>
        <p>{{Card.CVC}}</p>
        <!-- <p>{{Card.Vendor}}</p> -->
        
      </section>

      <CardForm
      @send="RITA"
      @ChangePage="$emit('ChangePage')"
      @AddtoList="AddtoList"
      />
      <!-- @submitted="$emit('submitted', this.Card)" -->
  </div>
</template>

<script>
import CardForm from './CardForm.vue'
import ninja from '../assets/ninja.svg'
import bitcoin from '../assets/bitcoin.svg'
import blockchain from '../assets/blockchain.svg'
import evil from '../assets/evil.svg'

export default {
    components: {CardForm},
    data(){return{
        currentUrl: ninja,
        // randomurl: bitcoin,blockchain,evil,
        Card: {
            Cardnumber: "",
            Cardholder: "",
            Month: "",
            Year: "",
            CVC: "",
            Vendor: "",
        },
    }},
    methods: {
        AddtoList(payload){
            this.$emit('AddtoList', payload)
        },
        RITA(janne){
        this.Card.Cardnumber = janne.Cardnumber       
        this.Card.Cardholder = janne.Cardholder       
        this.Card.CVC = janne.CVC       
        this.Card.Month = janne.Month    
        this.Card.Year = janne.Year
        if (janne.Vendor == "Blockchain"){
           this.currentUrl = blockchain 
           }
        if (janne.Vendor == "Ninja"){
           this.currentUrl = ninja
           }
        if (janne.Vendor == "Evil"){
           this.currentUrl = evil 
           }
        if (janne.Vendor == "Bitcoin"){
           this.currentUrl = bitcoin 
           }
        }
    }
}
</script>

<style scoped>
/* section {
    border:solid springgreen 1px;
} */

</style>