<template>
    <header>
        <nav class="navbar navbar-expand-lg navbar-light">
            <a class="navbar-brand" href="#"><img src="../assets/brand.svg" alt="brand-coinverser"> <span id="brand-text">Coinverter</span></a>
            <button type="button" class="navbar-toggler" data-toggle="collapse" data-target="#navbarCollapsible">
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
    padding: 0 10px;
}

.navbar{
    align-items: center;
}

.navbar-nav .nav-item{
    margin: 0 10px;
    font-size: 1.15rem;
}

.navbar-brand {
    font-size: 1.15rem;
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
    width: 65px;
    height: 25px;
    background-color: red;
    border-radius: 7px;
    border: 2px solid red;
    color: white;
    line-height: 20px;
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