<template>
      <ul>
        <CardItem 
        v-for="Card in Card" :key="Card.Cardnumber"
        :Card="Card"
        @ActiveCard="$emit('ActiveCard', Card)"
        />
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
  grid-auto-rows: 50px;
  padding: 0;
  margin: 8rem 0 6rem 0; 

}
</style>

