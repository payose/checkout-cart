<template>
  <div>
    <h1>My Cart</h1>

    <CartItemCard 
      v-for="product in products"
      :key="product.id"
      :product="product"
    />

    <CartPaymentCard
    />
  </div>
</template>

<script>
import CartItemCard from '@/components/cart/CartItemCard.vue'
import CartPaymentCard from '../components/cart/CartPaymentCard.vue'

export default {
  components: {
    CartItemCard,
    CartPaymentCard
  },
  computed: {
    products() {
      return this.$store.getters.cartItems
    }
  }
}
</script>