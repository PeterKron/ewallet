<template>
    <div>
        <form @submit.prevent="anyname">
            <label for="">CARD NUMBER</label>
            <input type="text" v-model.number="Cardnumber" @keyup="anyname">
            
            <label for="">CARDHOLDER NAME</label>
            <input type="text">
            
            <label for="">VALID THRU</label>
            <input type="text">
            
            <label for="">CVC</label>
            <input type="text">
            
            <label for="">VENDOR</label>
            <input type="text" >

            <button></button>
        </form>
    </div>
</template>

<script>

export default {
    data(){return{
        Cardnumber: "",
    }},
    methods: {
        anyname(){
            this.$emit('send', this.Cardnumber)
        }
    }
}
</script>
<style>
/* this.$emit('send', {...this.user}) */

</style>