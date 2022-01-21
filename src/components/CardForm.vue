<template>
<!-- form @submit.prevent="() => $emit('ChangePage'), (Card) => $emit('AddtoList', Card)" -->
 <div> 
        <form @submit.prevent="Submit">
            <label for="">CARD NUMBER</label>
            <input type="text" v-model="Card.Cardnumber" 
            @keyup="RenderCard">
            
            <label for="">CARDHOLDER NAME</label>
            <input type="text" v-model="Card.Cardholder" @keyup="RenderCard">
            
            <label for="">MONTH</label>
            <select v-model="Card.Month" @mouseup="RenderCard">
                <option v-for="month in 12" :key="month">
                    {{(month > 9) ? month : '0' + month}}
                </option>
            </select>

            <label for="">YEAR</label>
            <select v-model="Card.Year" @mouseup="RenderCard">
                <option v-for="year in 5" :key="year">
                    {{year + 21}}
                </option>
            </select>
            
            <label for="">CVC</label>
            <input type="number" v-model="Card.CVC" @keyup="RenderCard">
            
            <label for="">VENDOR</label>
            <select v-model="Card.Vendor" @mouseup="RenderCard">
                <option v-for="vendor in Vendors" :key="vendor.text">
                    {{vendor.text}}
                </option>
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
            Vendor: null,
        },
        Vendors: [{text: "Bitcoin",},
        {text: "Ninja", },
        {text: "Blockchain",},
        {text: "Evil", },
        ],
    }},
    methods: {
        Submit(){
            this.$emit('ChangePage')
            this.$emit('AddtoList', this.Card)
            // this.$emit('AddtoList', {...this.Card})
        },
        // add ifs and donts
        RenderCard(){
            if(this.Card.Cardnumber.length >= 4){
                console.log(2)
            }
            this.$emit('RenderCard', this.Card)        
        }
    }
}
</script>
<style>
/* this.$emit('send', {...this.user}) */

</style>