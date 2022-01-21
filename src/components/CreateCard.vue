<template>
  <div>
      <p>{{freg}}</p>
      <CardForm
      @send="RITA"
      />
  </div>
</template>

<script>
import CardForm from './CardForm.vue'

export default {
    components: {CardForm},
    data(){return{
        freg: "",
    }},
    methods: {
        RITA(janne){
        this.freg = janne       
        }
    }
}
</script>

<style>

</style>