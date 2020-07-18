<template>
    <div>
        <div class="row">
            <app-stock v-for="(stock,i) in stocks" :key="i" :stock="stock"></app-stock>
        </div>
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
        },
        created() {
        }
    }
</script>