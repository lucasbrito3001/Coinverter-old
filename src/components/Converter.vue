<template>
    <div class="converter col-12 col-md-8 m-auto">
        <div class="box">
            <img v-bind:src="require(`../assets/${moedaC}.png`)" alt="#" id="imgConverter"/>
            <h2><span class="currency">{{moedaC}}</span> para <span class="currency">{{moedaA}}</span> <img src="../assets/setas.svg" alt=""/> <input type="number" id="moeda-a" v-model="valueA" v-bind:placeholder="moedaC"></h2>
            <h3 id="res">
                {{inputA}} {{moedaC}} = {{valueC}} {{moedaA}}
            </h3>
        </div>
    </div>
</template>

<script>
export default {
    props: [ "moedaA" , "moedaC" , "moedaA_value" , "moedaC_value" , "inputMoedaA"],

    data(){
        return{
            valueA: this.moedaA_value,
            inputA: this.inputMoedaA,
            valueC: this.moedaC_value,
            cotacao: ""
        }
    },

    created(){
        setInterval( async () => {
            try {
                const response = await fetch(`https://economia.awesomeapi.com.br/all/${this.moedaC}-${this.moedaA}`)
                const data = await response.json()
                this.cotacao = data[this.moedaC].bid
                this.valueC = (this.valueA * this.cotacao).toFixed(2)
                this.inputA = this.valueA
            } catch (error) {
                console.log('[ERRO]')
            }
        }, 100);
    },

    methods:{
        converter(){
        },

        resetValue(){
            this.valueC = ''
        }
    }
    
}
</script>

<style scoped>
.converter{
    text-align: center;
    box-sizing: border-box;
}


h2{
  font-size: 1.4rem;
  margin-bottom: 2.5rem;
}

h3{
    font-size: 1.3rem;
    margin-top: 2.5rem;
}

input{
    height: 25px;
    padding: 5px;
    outline: none;
}

#moeda-a{
    text-align: center;
    border: none;
    border-bottom: 3px solid var(--result);
    font-size: 1.2rem;
    color: rgb(82, 82, 82);
    width: 150px;
    margin-left: 10px;
}

.box{
    margin: 15px 0;
    border-radius: 5px;
    padding: 10px 0;
}

.box h2 img{
    width: 10px;
    margin-left: 10px;
}

#res {
    color: rgb(82, 82, 82);
    border-bottom: 3px solid var(--result);
    width: fit-content;
    padding: 5px 0;
    box-sizing: border-box;
    margin: auto;
    font-size: 1.3rem;
}

#imgConverter{
    margin-bottom: 4.5vh;
}

.currency {
    color: var(--currency);
}
</style>