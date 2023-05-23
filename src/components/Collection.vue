<script setup>
import Card from './Card.vue';

// import Products from json
import productsJSON from '../assets/products.json'

//take data of 4 products
const productList = productsJSON.products.slice(4,8);

</script>

<template>
    <div class="container" >
        <Card v-for="(product,index) in productList" :key="index" :product="product"/>
    </div>
</template>