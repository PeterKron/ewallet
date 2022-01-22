<template>
      <ul>
        <CardItem 
        v-for="Card in Card" :key="Card.Cardnumber"
        :Card="Card"
        />
      </ul>
</template>

<script>

import CardItem from '../components/CardItem.vue'
export default {
  components: {CardItem},
  props: ['Card']
}
</script>

<style>
ul {
    padding: 0;
    /* margin: 0; */
}
</style>

