<template>
    <div class="quotes col-4 col-sm-4 col-md-4 col-lg-2 col-xl-2">
        <span>{{moedaB}} : <span v-bind:class="moedaB">{{cotacao}}%</span></span>
    </div>
</template>

<script>
export default {
    props: ["moedaA" , "moedaB"],

    data(){
        return{
            cotacao: "",
            time: 1000,
            verifyTime: 0
        }
    },

    created(){
        setInterval( async () => {
            try {
                const response = await fetch(`https://economia.awesomeapi.com.br/all/${this.moedaB}-${this.moedaA}`)

                const data = await response.json()
                this.cotacao = data[this.moedaB].pctChange
            } catch (error) {
                console.log('[ERRO]')
            }
            this.colorSpan()
        },this.time)
    },

    methods: {
        colorSpan(){
            const backgroundSpan = document.querySelector(`.${this.moedaB}`)
            backgroundSpan.classList.add('value')
            if(this.cotacao > 0){
                backgroundSpan.style.background = 'green'
            } else{
                backgroundSpan.style.background = 'red'           
            }
        }
    }
}
</script>

<style scoped>
.quotes{
    text-align: center;
}

span{
    font-size: .9rem;
}

.value{
    padding: .1rem .2rem;
    border-radius: 5px;
    color: white;
}
</style>