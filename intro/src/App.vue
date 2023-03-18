<template>
  <div id="app">
    <ProductAdd @add:product="addProduct"/>
    <ProductList :products="products"
    @delete:product="deleteProduct"
    @update:product = "updateProduct"/>
  </div>
</template>

<script>
import ProductAdd from './components/ProductAdd.vue';
import ProductList from './components/ProductList.vue'

export default {
  name: 'App',
  components: {
    ProductList,
    ProductAdd
},
  data(){
    return{
      products:[]
    }
  },
  methods:{
    deleteProduct(product){
      this.products = this.products.filter(
        productToFilter => productToFilter.id !== product.id
      )
    },
    updateProduct(product){

    },
    addProduct(product){
      const newProduct = {...product}
      this.products = [...this.products, newProduct]
      // this.products = [...this.products, product]
    },
    async getProducts(){
      const response = await fetch("http://localhost:3000/products")
      const data = await response.json()
      this.products = data;
    }
  },
  mounted(){
    this.getProducts();
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
