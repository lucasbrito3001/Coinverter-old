<template>
  <div id="app">
    <Header class="container.fluid"/>
    <main class="container">
      <section class="row" id="coinsQuotation">
        <Quotes moeda-a = "BRL" moeda-b = "USD"/>
        <Quotes moeda-a = "BRL" moeda-b = "EUR"/>
        <Quotes moeda-a = "BRL" moeda-b = "CAD"/>
        <Quotes moeda-a = "BRL" moeda-b = "BTC"/>
        <Quotes moeda-a = "BRL" moeda-b = "GBP"/>
        <Quotes moeda-a = "BRL" moeda-b = "CHF"/>
      </section>
      <section class="row" id="coinsConverter">
        <Converter moeda-a = "BRL" v-bind:moeda-c="moeda"/>
      </section>
      <section class="row" id="buttons">
        <Button moeda = "USD"></Button>
        <Button moeda = "EUR"></Button>
        <Button moeda = "BTC"></Button>
        <Button moeda = "CAD"></Button>
        <Button moeda = "CHF"></Button>
      </section>
    </main>
  </div>
</template>

<script>

import Converter from "./components/Converter.vue"
import Header from "./components/Header.vue"
import Quotes from "./components/Quotes.vue"
import Button from "./components/Button.vue"

export default {
  name: 'App',

  data(){
    return {
      moeda: "USD"
    }
  },

  components: {
    Header,
    Quotes,
    Converter,
    Button
  },

  methods: {
    changeMoedaC(){
      alert('enter')
    }
  }
}
</script>

<style>

:root {
  --border: #cfcfcf;
}

*{
  font-family: 'Ubuntu', sans-serif;
  box-sizing: border-box;
}

#coinsQuotation{
  border: .08rem solid var(--border);
  border-radius: .2rem;
  padding: .6rem;
  margin-top: 2vh;
}

#coinsConverter{
  margin-top: 8vh;
}

#buttons{
  display: flex;
  justify-content: space-evenly;
  max-width: 800px;
  margin: auto;
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
