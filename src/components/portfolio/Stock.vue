<template>
        <div class="col-sm-6 col-md-4">
            <div class="card text-white bg-info mb-3 mt-2">
                <div class="card-header">{{stock.name}}</div>
                <div class="card-body">
                    <h5 class="card-title">(Price: {{ stock.price}} | Quantity: {{stock.quantity}})</h5>
                    <div class="float-left">
                        <input type="number" 
                        class="form-control" 
                        placeholder="Quantity"
                        v-model.number="quantity"
                        :class="{danger: insufficientQuantity}">
                    </div>
                    <div class="float-right">
                        <button
                        class="btn btn-success"
                        @click="sellStock"
                        :disabled="insufficientQuantity || quantity <= 0 "
                        :class="{'mt-2' : insufficientQuantity}"
                        >{{insufficientQuantity ? 'Not enough Stocks' : 'Sell'}}
                        </button>
                    </div>
                </div>
            </div>
        </div>
</template>

<script>
    import {mapActions} from 'vuex';

    export default {
        props: ['stock'],
        data() {
            return {
                quantity: 0
            }
        },
        computed: {
            insufficientQuantity() {
                return this.quantity > this.stock.quantity;
            }
        },
        methods: {
            ...mapActions({
                placeSellOrder: 'sellStock'
            }),
            sellStock() {
                const order = {
                    stockId: this.stock.id,
                    stockPrice: this.stock.price,
                    quantity: this.quantity
                };
                this.placeSellOrder(order);
                this.quantity = 0;
            }
        }
    }
</script>

<style scoped>
    .danger {
        border: 1px solid red;
    }
</style>