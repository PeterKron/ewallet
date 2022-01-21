<template>
    <div>
        <form @submit.prevent="submit">
            <label for="">CARD NUMBER</label>
            <input type="number" v-model.number="Card.Cardnumber" @keyup="RenderCard">
            
            <label for="">CARDHOLDER NAME</label>
            <input type="text" v-model="Card.Cardholder" @keyup="RenderCard">
            
            <label for="">MONTH</label>
            <select v-model="Card.Month" @mouseup="RenderCard">
                <option v-for="month in Months" :key="month.text">
                    {{month.text}}
                </option>
            </select>

            <label for="">YEAR</label>
            <select v-model="Card.Year" @mouseup="RenderCard">
                <option v-for="year in Years" :key="year.text">
                    {{year.text}}
                </option>
            </select>
            
            <label for="">CVC</label>
            <input type="number" v-model="Card.CVC" @keyup="RenderCard">
            
            <label for="">VENDOR</label>
            <select v-model="Card.Vendor" @mouseup="RenderCard">
                <option>Bitcoin</option>
                <option>Ninja</option>
                <option>Blockchain</option>
                <option>Evil</option>
            </select>

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
            Month: "",
            Year: "",
            CVC: "",
            Vendor: "",
        },
        Months: [
            {text: "01"},{text: "02"},{text: "03"},{text: "04"},
            {text: "05"},{text: "06"},{text: "07"},{text: "08"},
            {text: "09"},{text: "10"},{text: "11"},{text: "12"},
        ],
        Years: [
            {text: "22"},{text: "23"},{text: "24"},{text: "25"},{text: "26"},
        ]
    }},
    methods: {
        submit(){
            this.$emit('ChangePage')
            this.$emit('AddtoList', this.Card)
            // this.$emit('submitted', {...this.Card})
        },
        // add ifs and donts
        RenderCard(){
            this.$emit('send', this.Card)
        }
    }
}
</script>
<style>
/* this.$emit('send', {...this.user}) */

</style>