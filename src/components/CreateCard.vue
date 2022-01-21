<template>
  <div>
      <p>{{this.Cardnumber}}</p>
      <p>{{this.Cardholder}}</p>
      <p>{{this.Valid}}</p>
      <p>{{this.CVC}}</p>
      <p>{{this.Vendor}}</p>
      <CardForm
      @send="RITA"
      />
  </div>
</template>

<script>
import CardForm from './CardForm.vue'

export default {
    components: {CardForm},
    data(){return{
        Cardholder: "",
        Cardnumber: "",
        Valid: "",
        CVC: "",
        Vendor: "",
    }},
    methods: {
        RITA(janne){
        this.Cardnumber = janne.Cardnumber       
        this.Cardholder = janne.Cardholder       
        this.CVC = janne.CVC       
        this.Vendor = janne.Vendor      
        this.Valid = janne.Valid      
        }
    }
}
</script>

<style>

</style>