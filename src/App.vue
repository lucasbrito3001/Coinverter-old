<template>
  <div id="app">
    <Header class="container.fluid"/>
    <main class="container">
      <section class="row" id="coinsQuotation">
        <p class="col-12">Alteração das Moedas em 24h</p>
        <ExchangeRate moeda-a = "BRL" moeda-b = "USD"/>
        <ExchangeRate moeda-a = "BRL" moeda-b = "EUR"/>
        <ExchangeRate moeda-a = "BRL" moeda-b = "CAD"/>
        <ExchangeRate moeda-a = "BRL" moeda-b = "BTC"/>
        <ExchangeRate moeda-a = "BRL" moeda-b = "GBP"/>
        <ExchangeRate moeda-a = "BRL" moeda-b = "CHF"/>
        <button type="button" class="navbar-toggler" data-toggle="collapse" data-target="#coinCaption" id="buttonCaption">Legenda das Moedas</button>
        <ul class="collapse navbar-collapse" id="coinCaption">
          <li class="col-6 col-lg-2"><span class="coins">USD</span> : Dólar Comercial</li>
          <li class="col-6 col-lg-2"><span class="coins">CAD</span> : Dólar Canadense</li>
          <li class="col-6 col-lg-2"><span class="coins">EUR</span> : Euro</li>
          <li class="col-6 col-lg-2"><span class="coins">BTC</span> : BitCoin</li>
          <li class="col-6 col-lg-2"><span class="coins">GBP</span> : Libra Esterlina</li>
          <li class="col-6 col-lg-2"><span class="coins">CHF</span> : Franco Suíço</li>
        </ul>
      </section>
      <section class="row" id="coinsConverter">
        <Converter moeda-a = "BRL" v-bind:moeda-c="moeda" moeda-a_value = "1" moeda-c_value = "0" input-moeda-a = ""/>
      </section>
      <section class="row" id="buttons">
        <h3 class="col-12">Mais Opções de Conversão</h3>
        <Button moeda = "USD" @change="moeda = 'USD'"></Button>
        <Button moeda = "EUR" @change="moeda = 'EUR'"></Button>
        <Button moeda = "BTC" @change="moeda = 'BTC'"></Button>
        <Button moeda = "CAD" @change="moeda = 'CAD'"></Button>
        <Button moeda = "CHF" @change="moeda = 'CHF'"></Button>
        <Button moeda = "GBP" @change="moeda = 'GBP'"></Button>
      </section>
    </main>
    <aside class="container">
      <section class="row" id="table">
        <CurrencyTable/>
      </section>
      <section class="row" id="aboutConverter">
        <AboutConverter/>
      </section>
      <!-- <section id="news">
        <News/>
      </section> -->
      <section id="aboutBitcoin">
        <AboutBitcoin/>
      </section>
    </aside>
    <Footer class="container.fluid"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Converter from "./components/Converter.vue"
import ExchangeRate from "./components/ExchangeRate.vue"
import Button from "./components/Button.vue"
import CurrencyTable from "./components/CurrencyTable.vue"
import AboutConverter from "./components/AboutConverter.vue"
// import News from "./components/News.vue"
import AboutBitcoin from "./components/AboutBitcoin.vue"
import Footer from "./components/Footer.vue"

export default {
  name: 'App',

  data(){
    return {
      moeda: "USD"
    }
  },

  methods: {
    methods: {
      darkmode(){
        if(this.verify == 0){
          document.body.style.setProperty('--neutralText','white')
          document.body.style.backgroundColor = 'rgb(0,0,22)'
          this.verify = 1
        } else{
          document.body.style.setProperty('--neutralText','black')
          document.body.style.backgroundColor = 'white'
          this.verify = 0
        }
      }
    }
  },

  components: {
    Header,
    ExchangeRate,
    Converter,
    Button,
    CurrencyTable,
    AboutConverter,
    // News,
    AboutBitcoin,
    Footer
  }
}
</script>

<style>

:root {
  --border: #cfcfcf;
  --result: rgb(9, 11, 78);
  --currency: rgb(15, 9, 104);
  --inputmoeda: rgb(231, 231, 241);
  --neutralText: black;
}

html,body{
  scroll-behavior: smooth;
  overflow-x: hidden;
}

*{
  font-family: 'Ubuntu', sans-serif;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

main{
  min-height: 88vh;
  margin-top: 12.5vh;
  box-sizing: border-box;
}

h2,h3,p, td, footer, #quotes{
  color: var(--neutralText);
}

#coinsQuotation{
  border-radius: .2rem;
  padding: .6rem;
  margin: 5vh 0px 0 0px;
}

#coinsQuotation p{
  border-bottom: 1px solid var(--border);
}

.navbar-collapse{
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  list-style: none;
  font-size: .79rem;
  padding: 0;
  text-align: center;
}

#buttonCaption{
  border-radius: 2px;
  font-size: .83rem;
  padding: 2px 4px;
  text-align: center;
  margin: 35px 0 10px 12px;
  outline: 0;
  background-color: white;
  border: .5px solid var(--currency);
  color: var(--currency);
}

.coins{
  color: var(--currency);
}

#coinsConverter{
  margin-top: 4.5vh;
}

#buttons{
  display: flex;
  justify-content: space-evenly;
  max-width: 800px;
  margin: 2vh auto;
}

#buttons h3{
  font-size: .9rem;
  font-weight: normal;
  width: fit-content;
  border-bottom: 1px solid var(--border);
}

#table{
  box-sizing: border-box;
  padding: 0;
}

@media (max-width:992px) {
  html {
    font-size: 15px;
  }
}

@media (max-width:768px){
  html {
    font-size: 14px;
  }
}

@media (max-width:570px){
  html {
    font-size: 12px
  }
}

</style>
