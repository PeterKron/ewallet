<template>
  <div class="card">
      <img src="../assets/wifi.svg" alt="">
      <img src="../assets/chip.svg" alt="">
      <img src="../assets/ninja.svg" alt="">
      <span>
        <h2>2624  4214  3123  3223</h2>
      </span>
      <span class="majsan">
      <p>CARDHOLDER NAME</p>
      <p>VALID THRU</p>
      </span>
      <span class="majsan">
      <p>fredrik fredriksson</p>
      <p>{{nyckel}}</p>
      
      </span>
  <AddNewCard />
  </div>
  
</template>

<script>
import AddNewCard from '../views/AddNewCard.vue'

export default {
  props: ['nyckel'],
  components: {AddNewCard}
}
</script>

<style scoped>
span {
    display: flex;
    flex-direction: row;
    justify-content: center;
}
.majsan {
    display: flex;
    justify-content: space-evenly;
}
h2 {
    margin-right: 20px;
}
</style>