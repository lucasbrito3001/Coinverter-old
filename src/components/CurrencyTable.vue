<template>
    <table>
        <thead>
            <tr>
                <th>Moeda</th>
                <th>Valor</th>
                <th>Alteração (%)</th>
                <th>Alta</th>
                <th>Baixa</th>
                <th>Delta</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>{{datas[0].name}}</td>
                <td>{{datas[0].value}}</td>
                <td>{{datas[0].pctChange}}</td>
                <td>{{datas[0].highValue}}</td>
                <td>{{datas[0].lowValue}}</td>
                <td>{{datas[0].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[1].name}}</td>
                <td>{{datas[1].value}}</td>
                <td>{{datas[1].pctChange}}</td>
                <td>{{datas[1].highValue}}</td>
                <td>{{datas[1].lowValue}}</td>
                <td>{{datas[1].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[2].name}}</td>
                <td>{{datas[2].value}}</td>
                <td>{{datas[2].pctChange}}</td>
                <td>{{datas[2].highValue}}</td>
                <td>{{datas[2].lowValue}}</td>
                <td>{{datas[2].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[3].name}}</td>
                <td>{{datas[3].value}}</td>
                <td>{{datas[3].pctChange}}</td>
                <td>{{datas[3].highValue}}</td>
                <td>{{datas[3].lowValue}}</td>
                <td>{{datas[3].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[4].name}}</td>
                <td>{{datas[4].value}}</td>
                <td>{{datas[4].pctChange}}</td>
                <td>{{datas[4].highValue}}</td>
                <td>{{datas[4].lowValue}}</td>
                <td>{{datas[4].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[5].name}}</td>
                <td>{{datas[5].value}}</td>
                <td>{{datas[5].pctChange}}</td>
                <td>{{datas[5].highValue}}</td>
                <td>{{datas[5].lowValue}}</td>
                <td>{{datas[5].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[6].name}}</td>
                <td>{{datas[6].value}}</td>
                <td>{{datas[6].pctChange}}</td>
                <td>{{datas[6].highValue}}</td>
                <td>{{datas[6].lowValue}}</td>
                <td>{{datas[6].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[7].name}}</td>
                <td>{{datas[7].value}}</td>
                <td>{{datas[7].pctChange}}</td>
                <td>{{datas[7].highValue}}</td>
                <td>{{datas[7].lowValue}}</td>
                <td>{{datas[7].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[8].name}}</td>
                <td>{{datas[8].value}}</td>
                <td>{{datas[8].pctChange}}</td>
                <td>{{datas[8].highValue}}</td>
                <td>{{datas[8].lowValue}}</td>
                <td>{{datas[8].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[9].name}}</td>
                <td>{{datas[9].value}}</td>
                <td>{{datas[9].pctChange}}</td>
                <td>{{datas[9].highValue}}</td>
                <td>{{datas[9].lowValue}}</td>
                <td>{{datas[9].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[10].name}}</td>
                <td>{{datas[10].value}}</td>
                <td>{{datas[10].pctChange}}</td>
                <td>{{datas[10].highValue}}</td>
                <td>{{datas[10].lowValue}}</td>
                <td>{{datas[10].varBid}}</td>
            </tr>
            <tr>
                <td>{{datas[11].name}}</td>
                <td>{{datas[11].value}}</td>
                <td>{{datas[11].pctChange}}</td>
                <td>{{datas[11].highValue}}</td>
                <td>{{datas[11].lowValue}}</td>
                <td>{{datas[11].varBid}}</td>
            </tr>
        </tbody>
    </table>    
</template>

<script>
export default {
    data(){
        return {
            nameCoins: ["BTC","USD","EUR","CAD","GBP","AUD","CHF","USDT","ARS","LTC","JPY","CNY"],
            datas: [] 
        }
    },

    created(){
        setInterval( async () => {
            this.fillTable()
        }, 1000);
    },

    methods: {
        async fillTable(){
            try {
                const response = await fetch("https://economia.awesomeapi.com.br/json/all")
                const data = await response.json()
                for(let coinInfo in this.nameCoins){
                    let coinCode = this.nameCoins[coinInfo]

                    let coinObject = {
                        name: data[coinCode].name,
                        code: data[coinCode].code,
                        value: data[coinCode].bid,
                        pctChange: data[coinCode].pctChange,
                        highValue: data[coinCode].high,
                        lowValue: data[coinCode].low,
                        varBid: data[coinCode].varBid}

                    this.datas.push(coinObject)
                }
            } catch (error) {
                console.log('[ERRO]')
            }
        }
    }
}
</script>

<style scoped>
table{
    width: 96%;
    margin: auto;
}

thead{
    background: var(--result);
    color: white;
}

thead th, td{
    font-weight: normal;
    padding: 5px 0 5px 5px;
    box-sizing: border-box;
}
</style>