<template>
    <header>
        <nav class="navbar navbar-expand-lg navbar-light">
            <a class="navbar-brand" href="#"><img src="../assets/brand.svg" alt="brand-coinverser"> <span id="brand-text">Coinverter</span></a>
            <button type="button" id="navheader-toggler" class="navbar-toggler" data-toggle="collapse" data-target="#navbarCollapsible">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div id="navbarCollapsible" class="collapse navbar-collapse">
                <ul class="navbar-nav">
                    <li class="nav-item"><a class="nav-link" href="#table">Tabela de Cotações</a></li>
                    <li class="nav-item"><a class="nav-link" href="#aboutConverter">Conversor de Moedas</a></li>
                    <!-- <li class="nav-item"><a class="nav-link" href="#news">Notícias Relevantes</a></li> -->
                    <li class="nav-item"><a class="nav-link" href="#aboutBitcoin">Bitcoin</a></li>
                </ul>
                
                <ul class="navbar-nav ml-auto">
                    <li class="nav-item">
                        <a href="#" class="nav-link" v-on:click="darkmode">Dark Mode <span class="on-off"><span class="text">Off</span><span class="alternate"></span></span></a>
                    </li>
                </ul>
            </div>
        </nav>
    </header>    
</template>

<script>
export default {
    data(){
        return{
            event: 'off'
        }
    },
    methods: {
        darkmode(){
            const alternate = document.querySelector('.alternate')
            const interruptor = document.querySelector('.on-off')
            const text = document.querySelector('.text')
            if(this.event == 'off'){
                alternate.style.float = "right"
                alternate.style.transition = "float .4s ease-out"
                interruptor.style.background = "yellowgreen"
                interruptor.style.border = "2px solid yellowgreen"
                text.innerText = "On"
                this.event = 'on'
                this.$emit('darkmode')
            } else{
                alternate.style.float = "left"
                interruptor.style.background = "red"
                interruptor.style.border = "2px solid red"
                text.innerText = "Off"
                this.event = 'off'
                this.$emit('darkmode')
            }
        }
    }
}
</script>

<style scoped>

header{
    top: 0;
    border-bottom: 6px solid var(--result);
    position: fixed;
    background: white;
    width: 100%;
    z-index: 100;
}

.navbar{
    align-items: center;
}

.navbar-nav .nav-item{
    margin: 0 10px;
    font-size: 1.15rem;
}

.nav-link{
    color: rgba(0,0,0,.65);
}

.navbar-brand {
    font-size: 1.15rem;
    color: black;
}


.navbar-brand #brand-text{
    position: relative;
    margin-left: 5px;
}

.navbar-brand img{
    width: 35px;
    height: 35px;
    margin: 0;
}

.navbar-toggler:focus{
    outline: .5px solid rgb(170, 170, 170);
}

/* INTERRUPTOR */

.on-off{
    padding: 0px;
    position: relative;
    display: inline-block;
    width: 55px;
    height: 22px;
    background-color: red;
    border-radius: 7px;
    border: 2px solid red;
    color: white;
    line-height: 17px;
}

.text{
    font-size: .9rem;
}

.alternate{
    position: relative;
    display: inline-block;
    width: 50%;
    height: 100%;
    float: left;
    background: white;
    border-radius: 5px;
}
</style>