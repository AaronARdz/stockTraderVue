<template>
        <div class="col-sm-6 col-md-4">
            <div class="card text-white bg-secondary mb-3 mt-2">
                <div class="card-header">{{stock.name}}</div>
                <div class="card-body">
                    <h5 class="card-title">(Price: {{ stock.price}})</h5>
                    <div class="float-left">
                        <input type="number" 
                        class="form-control" 
                        placeholder="Quantity"
                        v-model="quantity">
                    </div>
                    <div class="float-right">
                        <button
                        class="btn btn-success"
                        @click="buyStock"
                        >Buy
                        </button>
                    </div>
                </div>
            </div>
        </div>
</template>

<script>
    export default {
        props: ['stock'],
        data() {
            return {
                quantity: 0
            }
        }, 
        methods: {
            buyStock() {
                const order = {
                    stockId: this.stock.id,
                    stockPrice: this.stock.price,
                    quantity: this.quantity
                };
                console.log(order);
                this.quantity = 0;
            }
        }
    }
</script>