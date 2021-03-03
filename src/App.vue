<template>
  <div id="app">
    <Header @darkmode="darkmode" class="container.fluid"/>
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
          <li class="col-6 col-lg-2"><abbr title="Dólar Comercial"><span class="coins">USD</span> : Dólar Comercial</abbr></li>
          <li class="col-6 col-lg-2"><abbr title="Dólar Canadense"><span class="coins">CAD</span> : Dólar Canadense</abbr></li>
          <li class="col-6 col-lg-2"><abbr title="Euro"><span class="coins">EUR</span> : Euro</abbr></li>
          <li class="col-6 col-lg-2"><abbr title="Bitcoin"><span class="coins">BTC</span> : Bitcoin</abbr></li>
          <li class="col-6 col-lg-2"><abbr title="Libra Esterlina"><span class="coins">GBP</span> : Libra Esterlina</abbr></li>
          <li class="col-6 col-lg-2"><abbr title="Franco Suiço"><span class="coins">CHF</span> : Franco Suíço</abbr></li>
        </ul>
      </section>
      <section class="row" id="newConverter">
        <NewConverter/>
      </section>
    </main>
    <aside class="container">
      <section class="row" id="table">
        <CurrencyTable/>
      </section>
      <section class="row" id="aboutConverter">
        <AboutConverter/>
      </section>
      <section id="aboutBitcoin">
        <AboutBitcoin/>
      </section>
    </aside>
    <Footer class="container.fluid"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import ExchangeRate from "./components/ExchangeRate.vue"
import CurrencyTable from "./components/CurrencyTable.vue"
import AboutConverter from "./components/AboutConverter.vue"
import AboutBitcoin from "./components/AboutBitcoin.vue"
import Footer from "./components/Footer.vue"
import NewConverter from "./components/NewConverter.vue"

export default {
  name: 'App',

  data(){
    return {
      moeda: "USD",
      verify: 0
    }
  },

  methods: {
      darkmode(){
        event.preventDefault()
        if(this.verify == 0){
          document.body.style.setProperty('--neutralText','white')
          document.body.style.setProperty('--result','#606060')
          document.body.style.setProperty('--currency','blue')
          document.body.style.backgroundColor = 'rgb(0,0,5)'
          document.body.querySelector('#coinCaption').style.color = "white"
          for(let cont = 0; cont < 6; cont++){
            document.body.querySelectorAll('.quotes')[cont].style.color = "white"
            if(cont < 4){
              document.body.querySelectorAll('.nav-link')[cont].style.color = "white"
            }
          }
          document.body.querySelector('.navbar-brand').style.color = 'white'
          document.body.querySelector('header').style.backgroundColor = 'rgb(0,0,20)'
          document.body.querySelector('#navheader-toggler').style.backgroundColor = "rgba(255,255,255,.2)"
          this.verify = 1


        } else{
          document.body.style.setProperty('--neutralText','black')
          document.body.style.setProperty('--result','rgb(9,11,78)')
          document.body.style.setProperty('--currency','rgb(15,9,104)')
          document.body.style.backgroundColor = 'white'
          document.body.querySelector('#coinCaption').style.color = "black"
          for(let cont = 0; cont < 6; cont++){
            document.body.querySelectorAll('.quotes')[cont].style.color = "black"
            if(cont < 4){
              document.body.querySelectorAll('.nav-link')[cont].style.color = "rgba(0,0,0,.65)"
            }
          }
          document.body.querySelector('.navbar-brand').style.color = 'black'
          document.body.querySelector('header').style.backgroundColor = 'white'
          this.verify = 0
        }
    }
  },

  components: {
    Header,
    ExchangeRate,
    CurrencyTable,
    AboutConverter,
    AboutBitcoin,
    Footer,
    NewConverter
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
  background-color: var(--currency);
  border: .5px solid var(--currency);
  color: white;
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

abbr{
  text-decoration-line: none;
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
