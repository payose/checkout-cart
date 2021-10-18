<template>
  <div class="drawer">

    <div class="product-details" v-if="product">
      <h1>helo</h1>
      <h3 class="text-center">{{ product.name }}</h3>
      <p class="description">{{product.description }}</p>
      <h3 class="text-center"> ${{ product.price.toFixed(2) }}</h3>

      <div class="cart-total" v-if="productTotal">
        <h3>In Cart</h3>
        <h4> {{ productTotal }}</h4>
      </div>

      <div class="button-container"> 
        <button class="remove" @click="removeFromCart()">Remove</button>
        <button class="add" @click="addToCart()">Add</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    'product',
  ],

  computed: {
    productTotal() {
      return this.$store.getters.productQuantity(this.product)
    }
  },

  methods: {
    addToCart() {
      this.$store.commit('addToCart', this.product)
    },

    removeFromCart() {
      this.$store.commit('removeFromCart', this.product)
    }
  }
}
</script>
