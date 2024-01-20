<template>
  <div>
    <header>
      <button v-on:click="navigateTo('products')">View Products</button>
      {{ cart.length }} in cart
      <button v-on:click="navigateTo('cart')">View Cart</button>
    </header>

    <div v-if="page === 'cart'">
      <Cart v-on:removeItemFromCart="removeItemFromCart" :cart="cart" />
    </div>

    <div v-if="page === 'products'">
      <Products v-on:addItemToCart="addItemToCart" />
    </div>
  </div>
</template>

<script>
import Products from "./components/Products.vue";
import Cart from "./components/Cart.vue";

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
      this.cart.splice(this.cart.indexOf(product), 1);
    },
    navigateTo(page) {
      this.page = page;
    },
  },
  components: { Products, Cart },
}
</script>

<style>
body {
  margin: 0;
}

.products {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.products button {
  padding: 10px;
  background-color: white;
  color: black;
  outline: none;
  border: none;
  cursor: pointer;
}

</style>

<style scoped>

header {
  height: 60px;
  background-color: #eee;
  box-shadow: 2px 2px 10px pink;
  color: black;
  text-align: right;
  font-size: 30px;
  padding-top: 20px;
}

header button {
  margin: 20px;
  border: none;
  cursor: pointer;
  background-color: rgb(95, 110, 95);
  border-radius: 5px;
}
</style>
