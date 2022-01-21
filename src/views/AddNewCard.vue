<template>
  <main class="AddNewCard">
      <CardItem />
      <!-- <div>
          <p>{{CardNumber}}</p>
          <p>{{CardName}}</p>
          <p>{{ValidThru}}</p>
          <p>{{CVC}}</p>
      </div> -->
      <form @submit.prevent="anyname">
        <label for="">CARD NUMBER</label>
        <input type="text" v-model="CardNumber" @keyup="senddata">
        
        <label for="">CARDHOLDER NAME</label>
        <input type="text" v-model="CardName">
        
        <label for="">VALID THRU</label>
        <input type="text" v-model="ValidThru">
        
        <label for="">CVC</label>
        <input type="text" v-model="CVC">
          
        <label for="">VENDOR</label>
        <input type="text" >
      </form>
  </main>
</template>

<script>
export default {
    data(){return{
    user: {
        CardNumber: "",
        CardName: "",
        ValidThru: "",
        CVC: "",
        Vendor: "",   
    }
    }},
    methods: {
    anyname (){
        this.$emit('send', {...this.user})
    }}
}
</script>

<style scoped>
label {
    font-size: 1rem;
}
</style>