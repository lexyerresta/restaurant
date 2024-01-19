<template>
  <div>
    <header>
      <button v-on:click="navigateTo('products')">View Products</button>
      {{ cart.length }} in cart
      <button v-on:click="navigateTo('cart')">View Cart</button>
    </header>

    <div v-if="page === 'cart'">
      <h1>Your Cart</h1>
      <div class="products">
        <div v-for="product in cart" :key="product.name">
          {{ product.name }}
          <img :src="product.image" width="500px" />
          <div>{{ product.price }}</div>
          <button v-on:click="removeItemFromCart(product)">Remove from cart</button>
        </div>
      </div>
    </div>

    <div v-if="page === 'products'">
      <h1>Products</h1>
      <div class="products">
        <div v-for="product in products" :key="product.name">
          {{ product.name }}
          <img :src="product.image" width="500px" />
          <div>{{ product.price }}</div>
          <button v-on:click="addItemToCart(product)">Add to Cart</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => {
    return {
      page: "products",
      cart: [],
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
    }
  },
  methods: {
    addItemToCart(product) {
      this.cart.push(product)
    },
    removeItemFromCart(product) {
      this.cart.splice(this.cart.indexOf(product));
    },
    navigateTo(page) {
      this.page = page;
    },
  },
  components: {},
}
</script>

<style>
body {
  margin: 0;
}
</style>

<style scoped>
.products {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

header {
  height: 60px;
  background-color: #eee;
  box-shadow: 2px 2px 5px #999;
  color: black;
  text-align: right;
  font-size: 30px;
  padding-top: 20px;
}
</style>
