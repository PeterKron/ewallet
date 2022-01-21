<template>
  <main class="AddNewCard">
      <CreateCard
      @ChangePage="$emit('ChangePage', 'home')"
      @AddtoList="AddtoList"
      />
      <!-- @submitted="this.$emit('fesds')" -->
  </main>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'

export default {
    components: {CreateCard},
    methods: {
    AddtoList(payload){
        this.$emit('AddtoList', payload)
    }},

    data(){return{
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