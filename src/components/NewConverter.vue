<template>
    <div class="converter">
        <img src="require(../assets/)" alt="">
        <div class="selectCurrencies">
            <select id="originalCurrency">
                <option value="BRL">Real</option>
                <option value="USD" selected>Dólar Americano</option>
                <option value="EUR">Euro</option>
                <option value="CAD">Dólar Canadense</option>
                <option value="BTC">Bitcoin</option>
                <option value="GBP">Libra Esterlina</option>
                <option value="CHF">Franco Suíço</option>
            </select>
            <div id="switchCurrencies">
                <picture>
                    <source media="(min-width: 600px)" srcset="../assets/switchHorizontal.svg">
                    <img src="../assets/switchVertical.svg" alt="switch-icon">
                </picture>
            </div>
            <select id="convertedCurrency">
                <option value="BRL" selected>Real</option>
                <option value="USD">Dólar Americano</option>
                <option value="EUR">Euro</option>
                <option value="CAD">Dólar Canadense</option>
                <option value="BTC">Bitcoin</option>
                <option value="GBP">Libra Esterlina</option>
                <option value="CHF">Franco Suíço</option>
            </select>
        </div>
        <div class="conversionResult">
            <input type="number" id="inputOriginalCurrency">
            <span>Vale:</span>
            <input type="number" id="inputConvertedCurrency">
        </div>
    </div>    
</template>

<script>
export default {
    
}
</script>

<style scoped>
    *{
        padding: 0px;
        margin: 0px;
    }

    .converter{
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        width: 70%;
        margin: 15vh auto 0;
    }

    .selectCurrencies{
        display: grid;
        grid-template-columns: 2fr .5fr 2fr;
        grid-template-rows: 6vh;
        gap: 10px;
        grid-template-areas: 'oC sC cC';
        align-items: center;
    }

    #originalCurrency{
        grid-area: oC;
    }

    #switchCurrencies{
        grid-area: sC;
        height: 100%;
        width: 100%;
        margin: auto;
    }

    #switchCurrencies img{
        width: 100%;
        height: 100%;
        padding: 5px;
        display: block;
        margin: auto;
        border: 1px solid #ddd;
        border-radius: 5px;
    }

    #convertedCurrency{
        grid-area: cC;
    }

    #originalCurrency, #convertedCurrency{
        border-radius: 0px;
        padding: 0 10px;
        height: 100%;

    }

    .conversionResult{
        display: grid;
        grid-template-columns: 1fr .5fr 1fr;
        grid-template-rows: 5vh;
        grid-template-areas: 'iOC span iCC';
        width: 100%;
        margin-top: 5vh;
        align-items: center;
    }

    #inputOriginalCurrency{
        grid-area: iOC;
    }

    #inputConvertedCurrency{
        grid-area: iCC;
    }

    #inputOriginalCurrency, #inputConvertedCurrency{
        border-radius: 0px;
        border: 1px solid gray;
        padding: 15px;
        height: 100%;
    }

    .conversionResult span{
        display: block;
        font-size: 1.2rem;
        margin: auto;
        grid-area: span;
    }

    select:focus, input:focus{
        outline: none;
        border: 1px solid gray;
    }

    @media(max-width:998px){
        .converter{
            width: 90%;
        }
    }

    @media(max-width: 768px){
        .conversionResult{
            gap: 10px;
            grid-template-columns: 1fr;
            grid-template-rows: 5vh 5vh;
            grid-template-areas: 'iOC' 'iCC';
        }
        
        .conversionResult span{
            display: none;
        }
    }

    @media(max-width:600px){

        .selectCurrencies{
            grid-template-columns: 5fr 1fr;
            grid-template-rows: 5vh 5vh;
            gap: 10px;
            grid-template-areas: 'oC sC' 'cC sC';
        }

        #switchCurrencies img{
            width: 3rem;
        }
        .converter{
            margin: 10vh auto 0;
        }
    }
</style>