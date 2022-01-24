<template>
      <ul>
        <CardItem 
        v-for="Card in Card" :key="Card.Cardnumber"
        :Card="Card"
        @ActiveCard="$emit('ActiveCard', Card)"
        />
        <!-- <h1 v-if="Card == Array">you need to add cards, to do it press button below</h1> -->
      </ul>
</template>

<script>

import CardItem from '../components/CardItem.vue'
export default {
  components: {CardItem},
  props: ['Card'],
}
</script>

<style lang="scss" scoped>
ul {
  display: grid;
  grid-auto-rows: 20px;
  padding: 8rem;
  /* margin: 0; */

}
</style>

