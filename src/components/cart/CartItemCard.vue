<template>
  <div class="cart-item-card">
    <div class="header">
      <h3>{{ product.name}}</h3>
      <h4> In Cart: {{product.quantity }}</h4>
      <h4> Total Cost: {{ itemCost.toFixed() }}</h4>
    </div>
    <p> {{ description }}</p>
  </div>
</template>

<script>
export default {
  props: [
    'product'
  ],

  computed: {
    description() {
      return this.product.description.substring(0, 120)
    },

    itemCost(){
      return this.product.price * this.product.quantity
    }
  }
}
</script>