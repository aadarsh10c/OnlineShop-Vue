<script setup>
import Card from './Card.vue';
import {state} from '../App.vue'

console.log( state.productMap )

</script>

<template>
    <div class="container" >
        <Card v-for="[index,product] in productMap" :key="index" :product="product"/>
    </div>
</template>