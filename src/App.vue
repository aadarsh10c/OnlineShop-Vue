<script setup>
import Collection from './components/Collection.vue';
import userLogo from './assets/hulk_logo.svg'

</script>

<template>
  <header>
    <img alt="Hulk logo" class="logo" :src="userLogo" width="125" height="125" />

    <div class="wrapper">
      <h1 class="main-head">Featured Collection</h1>
      <p class="sub-head">Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi ad, assumenda adipisci illum rerum fugiat voluptatem fuga repellat ullam sapiente!</p>
    </div>
  </header>

  <main>
    <Collection/>
  </main>
</template>

