<script setup>
import closeLine from '../assets/close-line.svg'


</script>

<template>
    <div class="modal">
        <div class="modal-head">
            <div class="modal-title">
                <h1>
                    Your Bag
                </h1>
                <h2>
                    ( 2 item)
                </h2>
            </div>
            
            <div class="close-container" @click="$emit('closeModal')">
                <img :src="closeLine" alt="close button" class="close-img">
            </div>

        </div>
        <div class="modal-body">
            test
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