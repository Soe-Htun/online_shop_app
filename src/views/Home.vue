<template>
  <div class="home">
    <header>
       <button class="view" @click="navigateTo('products')">View Products</button>
      {{cart.length}} in cart
      <button class="view" @click="navigateTo('cart')">View Cart</button>
    </header>
    <div class="body">
      <div v-if="page === 'cart'">
        <cart v-on:removeItemFromCart="removeItemFromCart" :cart="cart"/>
      </div>

      <div v-if="page === 'products'">
          <product v-on:addItemToCart="addItemToCart" />
      </div>
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
import cart from '@/views/cart'
import product from './product'
export default {
  name: 'Home',
  components:{
    product,
    cart
  },
  data() {
    return {
      page:'products',
      cart:[],
    }
  },
  methods:{
    addItemToCart(product){
      this.cart.push(product);
      console.log(this.cart);
    },
    removeItemFromCart(product){
        this.cart.splice(this.cart.indexOf(product), 1)
    },
    navigateTo(page){
      this.page = page
    }
  }
  
}
</script>

<style scoped>
.body{
  overflow: hidden;
  overflow: -moz-scrollbars-none;
   /* this will hide the scrollbar in internet explorers */
  -ms-overflow-style: none;
  scrollbar-width: none;  /* Firefox */
}
.view{
  border: none;
  background-color: #46b824;
  color: white;
  height: 30px;
  width: 75px;
  vertical-align: middle;
  margin-right: 10px;
  border-radius: 20px;
}
header{
  height: 60px;
  background-color: #eee;
  text-align: right;
  box-shadow: 3px 4px 5px 2px #999;
  font-size: 30px;
  vertical-align: middle;
  line-height: 60px;
  position: fixed;
  width: 100%;
}
</style>