<template>
  <div id="app">
    <ProductList :products="products"
    @delete:product="deleteProduct"/>
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue'

export default {
  name: 'App',
  components: {
    ProductList
  },
  data(){
    return{
      products:[
        {
          id:1,
          categoryId:1,
          productName:"Laptop",
          quantityPerUnit:"Acer Laptop",
          unitPrice:5000,
          unitsInStock:2
        },
        {
          id:2,
          categoryId:1,
          productName:" Keyboard",
          quantityPerUnit:"HP Klavye",
          unitPrice:300,
          unitsInStock:13
        },
        {
          id:3,
          categoryId:2,
          productName:"Mouse",
          quantityPerUnit:"Logitech Mouse",
          unitPrice:125,
          unitsInStock:24
        }
      ],
    }
  },
  methods:{
    deleteProduct(product){
      this.products = this.products.filter(
        productToFilter => productToFilter.id !== product.id
      )
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
