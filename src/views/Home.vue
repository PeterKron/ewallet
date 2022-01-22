<template>
  <main class="Home">
    <h1>ALL MY SEXY CARDSSS</h1>
      <ul>
        <CardItem 
        v-for="Card in CardListData" :key="Card.Cardnumber"
        :Card="Card"
        />
      </ul>
  </main>
</template>

<script>

import CardItem from '../components/CardItem.vue'
export default {
  components: {CardItem},
  props: ['CardListData']
}
</script>

<style>
</style>

