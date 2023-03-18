<template>
    <div id="addForm">
        <form @submit.prevent="handleAdd">
            <div class="form-group"> 
                <label id="id">Id</label>
                <input type="text" v-model="product.id"
                class="form-control" id="id">
            </div>
            <div class="form-group"> 
                <label id="id">Product Name</label>
                <input type="text" v-model="product.productName"
                class="form-control" id="productName">
            </div>
            <div class="form-group"> 
                <label id="id">Category Id</label>
                <input type="text" v-model="product.categoryId"
                class="form-control" id="categoryId">
            </div>
            <div class="form-group"> 
                <label id="id">Description</label>
                <input type="text" v-model="product.quantityPerUnit"
                class="form-control" id="quantityPerUnit">
            </div>
            <div class="form-group"> 
                <label id="id">Unit Price</label>
                <input type="text" v-model="product.unitPrice"
                class="form-control" id="unitPrice">
            </div>
            <div class="form-group"> 
                <label id="id">Amount</label>
                <input type="text" v-model="product.unitInStock"
                class="form-control" id="unitInStock">
            </div>
            <button type="submit" class="btn btn-md btn-primary">
                Submit
            </button>
        </form>
    </div>
</template>
<script>
    export default {
        name:"product-add",
        data(){
            return{
                product:{
                    id:"",
                    categoryId:"",
                    productName:"",
                    quantityPerUnit:"",
                    unitPrice:"",
                    unitInStock:""
                }
            }
        },
        methods:{
            handleAdd(){
                this.$emit("add:product",this.product)
            }
        }
    }
</script>
<style scoped>
    #addForm{
        margin: 100px;
    }
</style>