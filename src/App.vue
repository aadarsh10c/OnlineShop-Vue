<script setup>
import { reactive,ref } from 'vue'

//import important components
import Card from './components/Card.vue'
import CartModal from './components/CartModal.vue'

import userLogo from './assets/hulk_logo.svg'
import cartLogo from './assets/shopping-bag.svg'

// import Products from json
import productsJSON from './assets/products.json'


//take data of 4 products and create a map with index as id
const productMap = new Map()
 productsJSON.products.slice(4,8).forEach( (product, index) => {
    let id = index;
    let obj={
        id,
        imageURL:product.images[1].src,
        title:product.title,
        price:product.variants[0].price,
        count:0
    }
    productMap.set(id , obj)
});

const state = reactive({
  productMap:productMap,
  totalItems: 0
})




//toggle for showing cart
const showCart = ref( false )
function setShowCart(){
  showCart.value = !showCart.value
}
function incrementCart( id ){
    if(state.productMap.has(id)){
      state.productMap.get(id).count++
      state.totalItems++
    } 
}

function decrementCart( id ){
    if(productMap.has(id)){
      state.productMap.get(id).count--
      state.totalItems--
    } 
}

function resetCount( id ){
  if(productMap.has(id)){
      state.totalItems -= state.productMap.get(id).count
      state.productMap.get(id).count = 0
    } 
}

</script>

<template>
  <div class="shop-container">
    <div v-if="showCart" class="modal-container">
      <CartModal @close-modal="setShowCart" @rem-from-cart="decrementCart" @add-to-cart="incrementCart" @remove-item="resetCount" :productMap="state.productMap" :total-items="state.totalItems"/>
    </div>
      <header>
        <div class="cart-box"  @click="setShowCart">
          <img :src="cartLogo" alt="Cart Logo" class="cart-icon">
          <div class="counter-container">
            <p class="counter">{{ state.totalItems }}</p>
          </div>
        </div>
        <img alt="Hulk logo" class="logo" :src="userLogo" width="125" height="125" />

        <div class="wrapper">
          <h1 class="main-head">Featured Collection</h1>
          <p class="sub-head">Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi ad, assumenda adipisci illum rerum fugiat voluptatem fuga repellat ullam sapiente!</p>
        </div>
    </header>

    <main>
      <div class="container">
        <Card v-for="[index,product] in state.productMap" :key="index" :product="product" @add-to-cart="incrementCart"/>
      </div>
    </main>
  </div>
</template>

