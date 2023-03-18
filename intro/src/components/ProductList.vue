<template>
    <div id="list">
        <p v-if="products.length == 0">
            Product list is empty!
        </p>
        <table v-else class="table">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Product Name</th>
                    <th>Category</th>
                    <th>Description</th>
                    <th>Unit Price</th>
                    <th>Amount</th>
                    <th></th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="product in products" :key="product.id">
                    <td v-if="updateId===product.id">
                        <input type="text" v-model="product.id"
                        class="form-control" id="id">
                    </td>
                    <td v-else>{{ product.id }}</td>
                    <td v-if="updateId===product.id">
                        <input type="text" v-model="product.productName"
                        class="form-control" id="productName">
                    </td>
                    <td v-else>{{ product.productName }}</td>
                    <td v-if="updateId===product.id">
                        <input type="text" v-model="product.categoryId"
                        class="form-control" id="categoryId">
                    </td>
                    <td v-else>{{ product.categoryId }}</td>
                    <td v-if="updateId===product.id">
                        <input type="text" v-model="product.quantityPerUnit"
                        class="form-control" id="quantityPerUnit">
                    </td>
                    <td v-else>{{ product.quantityPerUnit }}</td>
                    <td v-if="updateId===product.id">
                        <input type="text" v-model="product.unitPrice"
                        class="form-control" id="unitPrice">
                    </td>
                    <td v-else>{{ product.unitPrice }}</td>
                    <td v-if="updateId===product.id">
                        <input type="text" v-model="product.unitsInStock"
                        class="form-control" id="unitsInStock">
                    </td>
                    <td v-else>{{ product.unitsInStock }}</td>
                    <td v-if="updateId!==product.id">
                            <button
                            class="btn btn-sm btn-success mx-2" 
                            @click="handleUpdate(product)">
                                Update
                            </button>
                            <button
                            class="btn btn-sm btn-danger mx-2 " 
                            @click="handleDelete(product)">
                                -
                            </button>
                    </td>
                    <td v-else>
                            <button
                            class="btn btn-sm btn-success mx-2" 
                            @click="handleSave(product)">
                                Save
                            </button>
                            <button
                            class="btn btn-sm btn-danger mx-2" 
                            @click="updateId=null">
                                Remove
                            </button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>

    export default{
        name: "product-list",
        props:{
            products: Array
        },
        data(){
            return{
                updateId: null
            }
        },
        methods:{
            handleDelete(product){
                this.$emit("delete:product",product)
            },
            handleUpdate(product){
                this.updateId = product.id
            },
            handleSave(product){
                this.$emit("update:product",product),
                this.updateId = null
            }
        }
    }
</script>
<style scoped>
    #list{
        /* margin: 100px; */
    }
</style>