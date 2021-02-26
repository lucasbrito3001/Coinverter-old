<template>
    <div class="col-12">
        <button type="button" class="btn-primary" v-on:click="fillArray">Atualizar Tabela</button>
        <p>Ultima atualização: {{attTable}}</p>
        <table>
            <thead>
                <tr>
                    <th>Moeda</th>
                    <th>Valor</th>
                    <th>Alteração (%)</th>
                    <th>Alta</th>
                    <th>Baixa</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>{{datas[0].name}}</td>
                    <td>R$ {{datas[0].value}}</td>
                    <td>{{datas[0].pctChange}} %</td>
                    <td>R$ {{datas[0].highValue}}</td>
                    <td>R$ {{datas[0].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[1].name}}</td>
                    <td>R$ {{datas[1].value}}</td>
                    <td>{{datas[1].pctChange}} %</td>
                    <td>R$ {{datas[1].highValue}}</td>
                    <td>R$ {{datas[1].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[2].name}}</td>
                    <td>R$ {{datas[2].value}}</td>
                    <td>{{datas[2].pctChange}} %</td>
                    <td>R$ {{datas[2].highValue}}</td>
                    <td>R$ {{datas[2].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[3].name}}</td>
                    <td>R$ {{datas[3].value}}</td>
                    <td>{{datas[3].pctChange}} %</td>
                    <td>R$ {{datas[3].highValue}}</td>
                    <td>R$ {{datas[3].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[4].name}}</td>
                    <td>R$ {{datas[4].value}}</td>
                    <td>{{datas[4].pctChange}} %</td>
                    <td>R$ {{datas[4].highValue}}</td>
                    <td>R$ {{datas[4].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[5].name}}</td>
                    <td>R$ {{datas[5].value}}</td>
                    <td>{{datas[5].pctChange}} %</td>
                    <td>R$ {{datas[5].highValue}}</td>
                    <td>R$ {{datas[5].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[6].name}}</td>
                    <td>R$ {{datas[6].value}}</td>
                    <td>{{datas[6].pctChange}} %</td>
                    <td>R$ {{datas[6].highValue}}</td>
                    <td>R$ {{datas[6].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[7].name}}</td>
                    <td>R$ {{datas[7].value}}</td>
                    <td>{{datas[7].pctChange}} %</td>
                    <td>R$ {{datas[7].highValue}}</td>
                    <td>R$ {{datas[7].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[8].name}}</td>
                    <td>R$ {{datas[8].value}}</td>
                    <td>{{datas[8].pctChange}} %</td>
                    <td>R$ {{datas[8].highValue}}</td>
                    <td>R$ {{datas[8].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[9].name}}</td>
                    <td>R$ {{datas[9].value}}</td>
                    <td>{{datas[9].pctChange}} %</td>
                    <td>R$ {{datas[9].highValue}}</td>
                    <td>R$ {{datas[9].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[10].name}}</td>
                    <td>R$ {{datas[10].value}}</td>
                    <td>{{datas[10].pctChange}} %</td>
                    <td>R$ {{datas[10].highValue}}</td>
                    <td>R$ {{datas[10].lowValue}}</td>
                </tr>
                <tr>
                    <td>{{datas[11].name}}</td>
                    <td>R$ {{datas[11].value}}</td>
                    <td>{{datas[11].pctChange}} %</td>
                    <td>R$ {{datas[11].highValue}}</td>
                    <td>R$ {{datas[11].lowValue}}</td>
                </tr>
            </tbody>
        </table>
    </div>    
</template>

<script>
export default {
    data(){
        return {
            nameCoins: ["BTC","USD","EUR","CAD","GBP","AUD","CHF","USDT","ARS","LTC","JPY","CNY"],
            datas: [],
            storageArray: [],
            alternateFill: 0,
            attTable: ''
        }
    },

    created(){
        this.fillTable()
    },
    
    methods: {
        fillArray(){
            for(var deleteDatas = 0; deleteDatas <= 11 ; deleteDatas++){
                this.datas.pop()
            }
            console.log(this.datas)
            this.fillTable()
        },

        async fillTable(){
        try {
            const response = await fetch("https://economia.awesomeapi.com.br/json/all")
            const data = await response.json()
            let date = new Date()

            this.attTable = `${date.getDate()}/${date.getUTCMonth() + 1} - ${date.getHours()}:${date.getMinutes()}`
            for(let coinInfo in this.nameCoins){
                let coinCode = this.nameCoins[coinInfo]

                let coinObject = {
                    name: data[coinCode].name,
                    value: data[coinCode].bid,
                    pctChange: data[coinCode].pctChange,
                    highValue: data[coinCode].high,
                    lowValue: data[coinCode].low
                }

                this.datas.push(coinObject)
            } 
            console.log(this.datas)  
        } catch (error) {
            console.log('[ERRO]')
        }
    }
    }
}
</script>

<style scoped>

.col-12{
    padding: 0 5px;
}
table{
    width: 100%;
}

.btn-primary{
    margin-bottom: 2vh;
    border-radius: 5px;
    outline: none;
    border: none;
    padding: 0 5px;
}

.btn-primary:focus{
    outline: none;
    box-shadow: none;
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