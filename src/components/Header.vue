<template>
    <div>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <router-link class="navbar-brand" to="/" tag="a">Stock Trader</router-link>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <router-link class="nav-link" activeClass="active" to="/portfolio" tag="li">
                <a class="nav-link">Portfolio</a>
                </router-link>
                <router-link class="nav-link" activeClass="active" to="/stocks" tag="li">
                <a class="nav-link">Stocks</a>
                </router-link>
            </ul>
            <strong class="text-white">Funds: {{funds | currency}}</strong>
            <ul class="nav navbar-nav navbar-right">
                <li class="nav-item"><a class="nav-link" href="#" @click="endDay">End Day</a></li>   
                <li class="nav-item dropdown" 
                @click="isDropdownOpen = !isDropdownOpen"> 
                    <a class="nav-link dropdown-toggle" href="#"  data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    Save & Load
                    </a>
                    <div class="dropdown-menu" aria-labelledby="navbarDropdown" :class="{show: isDropdownOpen}"  >
                    <a class="dropdown-item" href="#" @click="saveData">Save</a>
                    <a class="dropdown-item" href="#" @click="loadData">Load</a>
                    </div>
                </li>
            </ul>
        </div>  
        </nav>
    </div>
</template>

<script>
    import {mapActions} from 'vuex';

    export default {
        data() {
            return {
                isDropdownOpen: false,
            }
        },
        computed: {
            funds() {
                return this.$store.getters.funds;
            }
        },
        methods: {
            ...mapActions({
                randomizeStocks: 'randomizeStocks',
                fetchData: 'loadData'
            }),
            endDay() {
                this.randomizeStocks();
            },
            saveData() {
                const data = {
                    funds: this.$store.getters.funds,
                    stockPortfolio: this.$store.getters.stockPortfolio,
                    stocks: this.$store.getters.stocks
                };
                this.$http.put('data.json',data);
            },
            loadData() {
                this.fetchData();
            }
        }
    }
</script>

<style scoped>

</style>