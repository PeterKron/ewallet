<template>
  <main class="AddNewCard">
      <CreateCard
      @ChangePage="$emit('ChangePage', 'home')"
      @AddtoList="(payload) => $emit('AddtoList', payload)"
      :CardListData="CardListData"
      />
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
</style>