<template>
  <main class="Home">
    <CardList 
    :CardListData="CardListData"    
    />
  </main>
</template>

<script>
import CardList from '../components/CardList.vue'
export default {
    components: {CardList},
    props: ['CardListData']
}
</script>

<style>

</style>