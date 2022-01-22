<template>
  <main class="Home">
      <ul>
        <CardItem 
        v-for="Card in Card" :key="Card.Cardnumber"
        :Card="Card"
        />
      </ul>
  </main>
</template>

<script>

import CardItem from '../components/CardItem.vue'
export default {
  components: {CardItem},
  props: ['Card']
}
</script>

<style>
</style>

