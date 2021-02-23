<template>
    <div class="converter col-12 col-md-8 m-auto">
        <div class="box">
            <h2>{{moedaC}} para {{moedaA}}</h2>
            <p>
                <input type="number" id="moeda-a" v-model="moedaA_value" v-bind:placeholder="moedaA">
                <button type="button" v-on:click="converter">Converter</button>
            </p>
            <h3>Resultado: {{moedaB_value}}</h3>
        </div>
    </div>
</template>

<script>
export default {
    props: [ "moedaA" , "moedaC" ],

    data(){
        return{
            moedaA_value: "",
            moedaB_value: 0.00,
            cotacao: ""
        }
    },

    async created(){
            try {
                const response = await fetch(`https://economia.awesomeapi.com.br/all/${this.moedaB}-${this.moedaA}`)
                const data = await response.json()
                this.cotacao = data[this.moedaB].bid

            } catch (error) {
                console.log('[ERRO]')
            }
    },

    methods:{
        converter(){
            this.moedaB_value = (this.moedaA_value * this.cotacao).toFixed(2)
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
}

h3{
    font-size: 1.4rem;
}

input{
    height: 25px;
    padding: 5px;
    outline: none;
}

.box{
    margin: 15px 0;
    border: 1px solid var(--border);
    border-radius: 5px;
    padding: 10px 0;
}

button{
    border-radius: 5px;
    border: .5px solid #ddd;
    outline: none;
    background: rgb(7, 0, 71);
    color: white;
    margin-left: 20px;
}
</style>