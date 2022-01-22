<template>
  <main class="AddNewCard">
      <CreateCard
      @ChangePage="$emit('ChangePage', 'home')"
      @AddtoList="(payload) => $emit('AddtoList', payload)"
      :CardListData="CardListData"
      />
      <!-- @submitted="this.$emit('fesds')" -->
  </main>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'

export default {
    props: ['CardListData'],
    components: {CreateCard},
}
</script>

<style scoped>
label {
    font-size: 1rem;
}
</style>