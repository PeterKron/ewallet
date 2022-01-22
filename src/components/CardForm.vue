<template>
<!-- form @submit.prevent="() => $emit('ChangePage'), (Card) => $emit('AddtoList', Card)" -->
 <div> 
        <form @submit.prevent="Submit">
            <label for="">CARD NUMBER</label>
            <input type="text" maxlength="19" v-model="Card.Cardnumber" autocomplete="cc-number"
            onkeypress="return /[1-9]/i.test(event.key)" @keyup="RenderCard" @keypress="AddSpace">
            
            <label for="">CARDHOLDER NAME</label>
            <input type="text" v-model="Card.Cardholder" maxlength="28"
            onkeypress="return /[a-ö,' ']/i.test(event.key)" @keyup="RenderCard">

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
            <input type="text" maxlength="3" v-model="Card.CVC" onkeypress="return /[1-9]/i.test(event.key)" >
            
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
            Vendor: "",
        },
        Vendors: [{text: "Bitcoin",},{text: "Ninja", },{text: "Blockchain",},{text: "Evil", },],
    }},
    methods: {
        Submit(){
            this.$emit('ChangePage')
            this.$emit('AddtoList', this.Card)
            // this.$emit('AddtoList', {...this.Card})
        },
        // add ifs and donts
        RenderCard(){
            this.$emit('RenderCard', this.Card)        
        },
        AddSpace (){
            if(this.Card.Cardnumber.length === 4 || this.Card.Cardnumber.length === 9 || this.Card.Cardnumber.length === 14){
                this.Card.Cardnumber += " "
            }
        }
    }
}
</script>
<style>
/* this.$emit('send', {...this.user}) */

/* .cardForm{
    margin: auto;
    width: 400px;
}
form{
    display: flex;
    flex-direction: column;
    width: 380px;
    margin-left: 10px;
    margin-top: 3rem;
}
label{
    align-self: flex-start;
    font-size: 12px;
    font-family: 'PT Mono', monospace;
}
input{
    border-radius: 5px;
    font-size: 18px;
    padding: 10px;
    border-width: 1px;
    margin-top: 5px;
    margin-bottom: 15px;
}
button{
    font-size: 22px;
    padding: 1rem;
    border-radius: 5px;
    margin-top: 2rem;
    border-width: 2px;
    background-color: white;
    font-weight: bold;
}
button:hover{
    background-color: black;
    color: white;
}
.validUntil{
    display: flex;
    flex-direction: column;
    input{
        width: 150px;
    }
}
.expireWrapper{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
} */
</style>