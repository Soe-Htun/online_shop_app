<template>
    <div class="cont">
        <h1>Products</h1>
        <div class="products">
          <div v-for="(product, index) in products" :key="index">
            <h4>{{ product.name }}</h4>
            <img :src="product.image" />
            <div>{{ product.cost }}</div>
            <button class="addtocart" @click="addItemToCart(product)">Add to cart</button>
        </div>
      </div>
    </div>
</template>
<script>
export default {
    name:'product',
    data() {
        return {
        page:'products',
        cart:[],
        products:[
            {
                name:"Hair Brush",
                cost:"$2.99",
                image:"https://pngimg.com/uploads/hairbrush/hairbrush_PNG116.png"
            },
            {
                name:"Cookies",
                cost:"$4",
                image:"https://www.congressionalschool.org/wp-content/uploads/2017/09/Cookies-PNG-Photos.png"
            },
            {
                name: "Pizza",
                cost:"$5",
                image:"https://www.pngkit.com/png/full/2-20221_pizza-png-image-pizza-seafood-png-top-view.png"
            },
            {
                name:"Hamburger",
                cost:"$4",
                image:"http://www.pngmart.com/files/5/Hamburger-PNG-Clipart.png"
            },
            {
                name:"Smart Watch",
                cost:"$10",
                image:"https://pngimage.net/wp-content/uploads/2018/06/smartwatch-png-3.png"
            },
            {
                name:"Chicken KFC",
                cost:"$1.2",
                image:"https://images.freshop.com/6950204/2a7c66cb8cff6105e486f1ebe24c053d_large.png"
            }
            ]   
        }
    },
    methods:{
        addItemToCart(product){
            console.log("here=>", product);
            this.$emit("addItemToCart", {...product});
        }
    }
}
</script>
<style scoped>
.addtocart{
  border: none;
  background-color: #409eff;
  color: white;
  height: 30px;
  width: 85px;
  border-radius: 20px;
}
.products{
    overflow-x: auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-row-gap: 30px;
     /* this will hide the scrollbar in mozilla based browsers */
    overflow: -moz-scrollbars-none;
   /* this will hide the scrollbar in internet explorers */
    -ms-overflow-style: none;
    scrollbar-width: none;  /* Firefox */
    margin-bottom: 25px;
}
.products::-webkit-scrollbar{
  display: none; 
}
img{
  width: 200px;
  height: 200px;
}
h4{
    text-shadow: 2px 4px 5px #999;
}
</style>