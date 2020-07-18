<template>
    <div>
        <div class="row">
            <app-stock v-for="(stock,i) in stocks" :stock="stock" :key="i"></app-stock>
        </div>
        <div class="row">
            <chart :options="stockPrices" autoresize />
        </div>
    </div>
</template>

<script>
    import {mapGetters, mapActions} from 'vuex';
    import Stock from './Stock.vue'
    import ECharts from 'vue-echarts'
    import 'echarts/lib/chart/bar'
    import 'echarts/lib/component/tooltip'


    export default {
        data() {
            return {
                values: {
                    title: {
                        text: 'StockMarket',
                        subtext: 'Obten dinero con solo 2 aplicaciones'
                    },
                    tooltip: {
                        trigger: 'axis',
                        axisPointer: {
                            type: 'shadow'
                        }
                    },
                    legend: {
                        data: ['Actual', 'Anterior']
                    },
                    grid: {
                        left: '3%',
                        right: '4%',
                        bottom: '3%',
                        containLabel: true
                    },
                    xAxis: {
                        type: 'value',
                        boundaryGap: [0, 0.01]
                    },
                    yAxis: {
                        type: 'category',
                        data: ['BMW', 'GOOGLE', 'FACEBOOK', 'TESLA', 'SPACEX']
                    },
                    series: [
                        {
                            name: 'Actual',
                            type: 'bar',
                            data: [0, 0, 0, 0, 0]
                        },
                        {
                            name: 'Valor en tu portfolio',
                            type: 'bar',
                            data: [0, 0, 0, 0, 0]
                        }
                    ]
                }
            }
        },
        components: {
            appStock: Stock,
            chart: ECharts
        },
        computed: {
            stocks() {
                return this.$store.getters.stocks;
            },
            stockPrices() {
                this.values.series[0].data = [
                    this.$store.getters.stocks[0].price,
                    this.$store.getters.stocks[1].price,
                    this.$store.getters.stocks[2].price,
                    this.$store.getters.stocks[3].price,
                    this.$store.getters.stocks[4].price
                ]
                this.values.series[1].data = [
                    this.portfolio.find(price => price.name === 'BMW') ? this.portfolio.find(price => price.name === 'BMW').price : 0,
                    this.portfolio.find(price => price.name === 'Google') ? this.portfolio.find(price => price.name === 'Google').price : 0,
                    this.portfolio.find(price => price.name === 'Facebook') ? this.portfolio.find(price => price.name === 'Facebook').price : 0,
                    this.portfolio.find(price => price.name === 'Tesla') ? this.portfolio.find(price => price.name === 'Tesla').price : 0,
                    this.portfolio.find(price => price.name === 'SpaceX') ? this.portfolio.find(price => price.name === 'SpaceX').price : 0,
                ]
                return this.values;
            },
            ...mapGetters({
                portfolio: 'stockPortfolio'
            })
        },
        created() {
           
        }
    }
</script>