<template>
    <div>
        <form @submit.prevent="anyname">
            <label for="">CARD NUMBER</label>
            <input type="text" v-model.number="Card.Cardnumber" @keyup="anyname">
            
            <label for="">CARDHOLDER NAME</label>
            <input type="text" v-model="Card.Cardholder" @keyup="anyname">
            
            <label for="">VALID THRU</label>
            <input type="text" v-model="Card.Valid" @keyup="anyname">
            
            <label for="">CVC</label>
            <input type="text" v-model="Card.CVC" @keyup="anyname">
            
            <label for="">VENDOR</label>
            <input type="text" v-model="Card.Vendor" @keyup="anyname">

            <button>ADD CARD</button>
        </form>
    </div>
</template>
<script>
export default {
    data(){return{
        Card: {
            Cardnumber: "",
            Cardholder: "",
            Valid: "",
            CVC: "",
            Vendor: "",

        }
    }},
    methods: {
        anyname(){
            this.$emit('send', this.Card)
        }
    }
}
</script>
<style>
/* this.$emit('send', {...this.user}) */

</style>