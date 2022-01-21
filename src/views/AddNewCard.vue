<template>
  <main class="AddNewCard">
      <CreateCard 
      />
  </main>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'

export default {
    components: {CreateCard},
    
    data(){return{
    user: {
        CardNumber: "",
        CardName: "",
        ValidThru: "",
        CVC: "",
        Vendor: "",   
    }
    }}
    // methods: {
    // anyname (){
    //     this.$emit('send', {...this.user})
    // }}
}
</script>

<style scoped>
label {
    font-size: 1rem;
}
</style>