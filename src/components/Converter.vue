<template>
    <div class="converter col-12 col-md-8 m-auto">
        <div class="box">
            <h2><span class="currency">{{moedaC}}</span> para <span class="currency">{{moedaA}}</span><input type="number" id="moeda-a" v-model="valueA" v-bind:placeholder="moedaC"></h2>
            
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
    background: var(--inputmoeda);
    border-radius: 2px;
    color: var(--result);
    box-shadow: .5px .5px 2px gray;
    width: 200px;
    margin-left: 15px;
}

.box{
    margin: 15px 0;
    border-radius: 5px;
    padding: 10px 0;
}

button{
    border-radius: 5px;
    border: .5px solid #ddd;
    outline: none;
    background: var(--result);
    color: white;
    margin-left: 20px;
}

#res {
    color: var(--result);
    border: 1px solid var(--border);
    background: var(--inputmoeda);
    max-width: 100%;
    padding: 5px 0;
    box-sizing: border-box;
    margin: auto;

}

.currency {
    color: var(--currency);
}
</style>