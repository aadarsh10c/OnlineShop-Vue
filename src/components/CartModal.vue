<script setup>
import closeLine from '../assets/close-line.svg'
import smallClose from '../assets/close-line-small.svg'
const props = defineProps({
    productMap: Map,
    totalItems: Number
})

</script>

<template>
    <div class="modal">
        <div class="modal-head">
            <div class="modal-title">
                <h1>
                    Your Bag
                </h1>
                <h2>
                    ( {{ props.totalItems }} {{ props.totalItems <= 1 ? 'item' : 'items'  }})
                </h2>
            </div>
            
            <div class="close-container" @click="$emit('closeModal')">
                <img :src="closeLine" alt="close button" class="close-img">
            </div>

        </div>
        <div class="modal-body">
            <template v-for="[index,product] in props.productMap">
                <div class="modal-item"  :key="index" v-if="product.count>0" >
                    <div class="item-info">
                        <div class="item-image-box">
                            <img :src="product.imageURL" alt="" class="item-image">
                        </div>
                        <div class="item-desc">
                            <h3>{{ product.title }}</h3>
                            <p class="item-btn">
                                <span @click="$emit('remFromCart',product.id)" class="minus">-</span><span>{{ product.count }}</span><span @click="$emit('addToCart',product.id)" class="plus">+</span>
                            </p>
                        </div>
                    </div>
                    <div class="item-price">
                        <div @click="$emit('removeItem', product.id)" class="remove-btn-container">
                            <img  :src="smallClose" alt="Remove Item">
                        </div>
                        <h3>${{ product.price }}</h3>
                    </div>
                </div>
            </template >
        </div>
        <div class="modal-footer">
            <div class="checkout-head">
                <h1 class="checkout-title">SUBTOTAL</h1>
                <h1 class="checkout-price">$131.98</h1>
            </div>

            <button class="checkout-button">
                &#x1F6D2;
                checkout
            </button>
            <div class="checkout-footer">
                <p>
                    Have a promo code?Enter your code at checkout.
                    Shipping and taxes are calcuated durin checkout.
                </p>
            </div>
        </div>
    </div>
</template>