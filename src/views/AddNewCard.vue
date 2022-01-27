<template>
  <main>
      <h1>ADD A NEW BANK CARD</h1>
      <CardItem 
      :Card="Card" 
      />
      <CardForm
      @RenderCard="RenderCard"
      @ChangePage="$emit('ChangePage', 'home')"
      @AddtoList="(payload) => $emit('AddtoList', payload)"
      :CardListData="CardListData"
      />
  </main>
</template>

<script>
import CardItem from '../components/CardItem.vue'
import CardForm from '../components/CardForm.vue'

export default {
    props: ['CardListData'],
    components: {CardForm, CardItem},
    data(){return{
        Card: {
            Vendor: "original"
        },
    }},
    methods: {
        RenderCard(Card){
        this.Card = Card
        }
    }
}
</script>

<style lang="scss">
</style>
