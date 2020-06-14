<template>
    <div>
        <h1>Trade Or view your portfolio</h1>
        <h6>You may save & load your Data</h6>
        <h6>Click on End day to begin new day</h6>
        <hr>
        <p>Your Funds: {{ funds | currency}}</p>
    </div>
</template>

<script>
export default {
    computed: {
        funds() {
            return this.$store.getters.funds;
        }
    }
}
</script>