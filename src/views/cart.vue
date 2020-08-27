<template>
    <div>
      <h1>Your Cart</h1>
      <div class="products">
          <div v-for="(product, index) in cart" :key="index">
            <h4>{{ product.name }}</h4>
            <img :src="product.image" />
            <div>{{ product.cost }}</div>
            <button class="addtocart" @click="removeItemFromCart(product)">Remove from cart</button>
        </div>
      </div>
    </div>
</template>
<script>
export default {
    name:'cart',
    props:["cart"],
    data() {
        return {
            
        }
    },
    methods:{
        removeItemFromCart(product){
            this.$emit("removeItemFromCart", product)  
        },
    }
}
</script>

<style scoped>
.addtocart{
  border: none;
  background-color: #e40404;
  color: white;
  height: 30px;
  width: 85px;
  border-radius: 20px;
}
.products{
    overflow: auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-row-gap: 30px;
     /* this will hide the scrollbar in mozilla based browsers */
    overflow: -moz-scrollbars-none;
   /* this will hide the scrollbar in internet explorers */
    -ms-overflow-style: none;
    scrollbar-width: none;  /* Firefox */
    margin-bottom: 25px;
    height: 100%;
}
img{
  width: 200px;
  height: 200px;
}
</style>