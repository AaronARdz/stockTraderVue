<template>
    <div>
        <app-stock v-for="(stock,index) in stocks" :key="index" :stock="stock"></app-stock>
    </div>
</template>

<script>
    import {mapGetters, mapActions} from 'vuex';
    import Stock from './Stock.vue'

    export default {
        computed: {
            ...mapGetters({
                stocks: 'stockPortfolio'
            })
        },
        components: {
            appStock: Stock
        }
    }
</script>