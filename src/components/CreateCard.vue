<template>
  <div>
      <section>
        <p>{{this.Card.Cardnumber}}</p>
        <p>{{this.Card.Cardholder}}</p>
        <p>{{this.Card.Month}}</p>
        <p>{{this.Card.Year}}</p>
        <p>{{this.Card.CVC}}</p>
        <p>{{this.Card.Vendor}}</p>
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

export default {
    components: {CardForm},
    data(){return{
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
        this.Card.Vendor = janne.Vendor      
        this.Card.Month = janne.Month    
        this.Card.Year = janne.Year      
        }
    }
}
</script>

<style scoped>
/* section {
    border:solid springgreen 1px;
} */

</style>