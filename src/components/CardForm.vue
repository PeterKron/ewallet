<template>
<!-- form @submit.prevent="() => $emit('ChangePage'), (Card) => $emit('AddtoList', Card)" -->
 <main> 
        <form @submit.prevent="Submit">
            
            <label for="">CARD NUMBER</label>
            <input type="text" maxlength="19" v-model="Card.Cardnumber"
            onkeypress="return /[1-9]/i.test(event.key)" @keyup="RenderCard" @keypress="AddSpace">
            
            
            <label for="">CARDHOLDER NAME</label>
            <input type="text" v-model="Card.Cardholder" maxlength="28"
            onkeypress="return /[a-ö,' ']/i.test(event.key)" @keyup="RenderCard">

            <section class="valid">
                <aside>
                    <label for="">MONTH</label>
                    <select v-model="Card.Month" @mouseup="RenderCard">
                        <option v-for="month in 12" :key="month">
                            {{(month > 9) ? month : '0' + month}}
                        </option>
                    </select>
                </aside>

                <aside>
                    <label for="">YEAR</label>
                    <select v-model="Card.Year" @mouseup="RenderCard">
                        <option v-for="year in 5" :key="year">
                            {{year + 21}}
                        </option>
                    </select>
                </aside>

                <aside>
                    <label for="">CVC</label>
                    <input type="text" maxlength="3" v-model="Card.CVC" onkeypress="return /[1-9]/i.test(event.key)" >
                </aside>
            </section>
            
            
            <label for="">VENDOR</label>
            <select v-model="Card.Vendor" @mouseup="RenderCard">
                <option v-for="vendor in Vendors" :key="vendor.text">
                    {{vendor.text}}
                </option>
            </select>
            <button>ADD CARD</button>
        </form>
    </main>
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
        // add ifs and donts
        Submit(){
            this.$emit('ChangePage')
            this.$emit('AddtoList', this.Card)
            // this.$emit('AddtoList', {...this.Card})
        },
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
/* this.$emit('send', {...this.user}) */
</script>
<style lang="scss">

form{
    display: flex;
    flex-direction: column;
    width: 382px;
    margin-top: 40px;
}
input, select {
    padding: 20px;
    border-radius: 5px;
    border-width: 1px;
    font-size: 18px;
    margin: 5px 0px 15px 0px;
}
aside {
    display: flex;
    flex-direction: column;
    margin-right: 12px;
    select {
        width: 100px;
    }
    input:first-of-type {
        width: 114px
    }
}
.valid {
    display: flex;
}
button {
    padding: 20px;
    border-radius: 5px;
    border-width: 1px;
    font-size: 22px;
    margin-top: 40px;
    background-color: white;
    font-weight: bold;
}
button:hover{
    background-color: black;
    color: white;
}
</style>