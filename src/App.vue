<script setup>
import { reactive,ref } from 'vue'

//import important components
import Collection from './components/Collection.vue'
import CartModal from './components/CartModal.vue'

import userLogo from './assets/hulk_logo.svg'
import cartLogo from './assets/shopping-bag.svg'

// import Products from json
import productsJSON from './assets/products.json'

const state = reactive({
  productMap:new Map()
})

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
    state.productMap.set(id , obj)
});



//toggle for showing cart
const showCart = ref( true )
function setShowCart(){
  showCart.value = !showCart.value
}
function incrementCart( id ){
    if(state.productMap.has(id)){
      console.log( 'its working')
      state.productMap.get(id).count++
    } 
}

function decrementCart( id ){
    if(productMap.has(id)){
      state.productMap.get(id).count--
    } 
}
</script>

<template>
  <div class="shop-container">
    <div v-if="showCart" class="modal-container">
      <CartModal @close-modal="setShowCart"/>
    </div>
      <header>
        <div class="cart-box"  @click="setShowCart">
          <img :src="cartLogo" alt="Cart Logo" class="cart-icon">
          <div class="counter-container">
            <p class="counter">0</p>
          </div>
        </div>
        <img alt="Hulk logo" class="logo" :src="userLogo" width="125" height="125" />

        <div class="wrapper">
          <h1 class="main-head">Featured Collection</h1>
          <p class="sub-head">Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi ad, assumenda adipisci illum rerum fugiat voluptatem fuga repellat ullam sapiente!</p>
        </div>
    </header>

    <main>
      <Collection />
    </main>
  </div>
</template>

