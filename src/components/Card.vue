<script setup>
const props = defineProps({
    product: Object
})

</script>

<template>
    <div class="card">
            <div class="pic-container">
                <img :src="props.product.images[1].src" alt="Dress Photo" class="pic">
            </div>
            <div class="card-desc">
                <div class="info">
                    <h3>{{ props.product.title }}</h3>
                    <h3>${{ props.product.variants[0].price }}</h3>
                </div>
            </div>
            <button class="btn btn-text">Add to cart</button>
        </div>
</template>