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

<style>
ul {
    padding: 0;
    /* margin: 0; */
}
</style>

