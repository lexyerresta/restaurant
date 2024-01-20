<template>
  <div>
    <h1>Your Cart</h1>
    <div class="products">
      <div v-for="(product, index) in cart" :key="index">
        <h3>{{ product.name }}</h3>
        <img :src="product.image" width="300px" />
        <div>{{ product.price }}</div>
        <button v-on:click="removeItemFromCart(index)">Remove from cart</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["cart"],
  methods: {
    removeItemFromCart(product) {
      this.$emit("removeItemFromCart", product);
    }
  }
};
</script>

<style></style>