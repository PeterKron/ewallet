<template>
 <main> 
        <form @submit.prevent="Submit">    
            <label for="">CARD NUMBER</label>
            <p class="error" v-if="errorcardnum == true">Cardnumber already exists</p>
            <p class="error" v-if="errorcardnumlength == true">Cardnumber must be 16 digits</p>
            <input type="text" maxlength="19" v-model="Card.Cardnumber"
            onkeypress="return /[1-9]/i.test(event.key)" 
            @keyup="RenderCard" @keypress="AddSpace" 
            @focus="(errorcardnumlength = false), (errorcardnum = false)">
             
            <label for="">CARDHOLDER NAME</label>
            <p class="error" v-if="errorcardname == true">We need both a first and lastname</p>
            <input type="text" v-model="Card.Cardholder" maxlength="28"
            onkeypress="return /[a-ö,' ']/i.test(event.key)" @keyup="RenderCard"
            @focus="errorcardname = false">

            <section class="valid">
                <aside>
                    <label for="">MONTH</label>
                    <select v-model="Card.Month" @change="RenderCard">
                        <option v-for="month in 12" :key="month">
                            {{(month > 9) ? month : '0' + month}}
                        </option>
                    </select>
                 <!-- <p class="error" v-if="errorcardnum == true">Fill out correct expiry month</p> -->
                </aside>
                <aside>
                    <label for="">YEAR</label>
                    <select v-model="Card.Year" @change="RenderCard">
                        <option v-for="year in 5" :key="year">
                            {{year + 21}}
                        </option>
                    </select>
                <!-- <p class="error" v-if="errorcardnum == true">Fill out correct expiry year</p> -->
                </aside>
                <aside>
                    <label for="">CVC</label>
                    <input type="text" maxlength="3" v-model="Card.CVC" onkeypress="return /[1-9]/i.test(event.key)" >
                    <!-- <p class="error" v-if="errorcardnum == true">You need to enter a CVC code</p> -->
                </aside>
            </section>

            <label for="">CARD TYPE</label>
            <select v-model="Card.Vendor" @change="RenderCard">
                <option v-for="vendor in Vendors" :key="vendor.text" :value="vendor.value">
                    {{vendor.text}}
                </option>
            </select>
            <!-- <p class="error" v-if="errorcardnum == true">Please choose a cardprovider</p> -->
            <button>ADD CARD</button>
        </form>
    </main>
</template>

<script>
export default {
    props: {CardListData:Array},
    data(){return{
        Card: {
            Cardnumber: "",
            Cardholder: "",
            Month: "",
            Year: "",
            CVC: "",
            Vendor: "",
        },
        errorlist: [],
        errorcardname: false,
        errorcardnum:  false,
        errorcardnumlength: false,
        Vendors: [{text: "Bitcoin Inc", value: "Bitcoin"},{text: "Ninja Bank", value: "Ninja"},
        {text: "Blockchain Inc", value: "Blockchain"},{text: "Evil Corp", value: "Evil" },],
    }},
    methods: {
        // add ifs and donts
        Submit(){
            this.errorlist = []
            if(this.Card.Cardnumber.length < 19 ){
                this.errorcardnumlength = true
                this.errorlist.push('cardnumlength')
            }
            if (this.CardListData.find((cardnum) => cardnum.Cardnumber == this.Card.Cardnumber)){
                this.errorcardnum = true
                this.errorlist.push('cardnumlength')
            }
            if (!this.Card.Cardholder.includes(" ") || this.Card.Cardholder.endsWith(" ") || this.Card.Cardholder.startsWith(" ")){
                this.errorcardname = true
                this.errorlist.push('cardnumlength')
            }
            if (!this.errorlist.length) {
                this.$emit('ChangePage')
                this.$emit('AddtoList', this.Card)
            }
        },
        RenderCard(){
            this.$emit('RenderCard', {...this.Card})        
        },
        AddSpace (){
            if(this.Card.Cardnumber.length === 4 || this.Card.Cardnumber.length === 9 || this.Card.Cardnumber.length === 14){
                this.Card.Cardnumber += " "
            }
        }
    }
}
</script>
<style lang="scss">
.error {
    color: red;
    font-size: 12px;
    text-shadow: -0.5px -0.5px rgba(0, 0, 0, 0.55);
}
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
select {
//   -webkit-appearance: none; 
}
//   <------- tar bort pilen
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
    p {
        margin: -14px 0px 10px 2px;
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