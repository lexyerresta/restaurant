<template>
  <div>
    <h1>Products</h1>
    <div class="products">
      <div v-for="(product, index) in products" :key="index">
        <h3>{{ product.name }}</h3>
        <div class="cost">{{ product.price }}</div>
        <img :src="product.image" width="300px" />
        <button v-on:click="addItemToCart(product)">Add to Cart</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      products: [
        {
          name: "Burger",
          price: "Rp.78.000",
          image:
            "https://img.kurio.network/QxKbt870DH97dKwzrHdsVy2S3Lw=/1200x1200/filters:quality(80)/https://kurio-img.kurioapps.com/21/09/01/66145feb-79af-4e77-ac79-32af2f70faee.jpe",
        },
        {
          name: "Quesadilla",
          price: "Rp.35.000",
          image:
            "https://recipetineats.com/wp-content/uploads/2018/06/Vegetable-Quesadilla.jpg",
        },
      ],
    };
  },
  methods: {
    addItemToCart(product) {
      this.$emit("addItemToCart", product);
    }
  }
}
</script>

<style></style>
