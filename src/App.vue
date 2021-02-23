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
        <Converter moeda-a = "BRL" moeda-b = "USD"/>
        <Converter moeda-a = "BRL" moeda-b = "CAD"/>
        <Converter moeda-a = "BRL" moeda-b = "EUR"/>
        <Converter moeda-a = "BRL" moeda-b = "BTC"/>
      </section>
    </main>
  </div>
</template>

<script>
import Converter from "./components/Converter.vue"
import Header from "./components/Header.vue"
import Quotes from "./components/Quotes.vue"
export default {
  name: 'App',
  components: {
    Header,
    Quotes,
    Converter
  }
}
</script>

<style>

:root {
  --border: #adadad;
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
