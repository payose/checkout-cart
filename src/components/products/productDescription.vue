<template>
  <!-- <div class="drawer-background" :class="{show: active}" @ckick="$emit('close-product-drawer')">
    
  </div> -->

  <div class="drawer" :class="{show: active}">
    <div class="drawer-close" @click="$emit('close-product-drawer')">
      X
    </div>

    <div class="product-details" v-if="product">
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
    'active'
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

<style scoped>
.drawer-background {
  width: 100%;
  height: 100vh;
  position: fixed;
  left: 0;
  top: 0;
  background-color:  rgba(204, 241, 156, 0.644);
  z-index: 100;
  display: none;
  transition: display .5s;
}

.drawer-background.show {
  display: block ;
}

.drawer{
  width: 95vw;
  height: 100vh;
  background-color: #fff;
  position: fixed;
  top: 0;
  left: -105vw;
  padding: 15px;
  transition: left .5s;
  z-index: 110;
  overflow-y: scroll;
}

.drawer.show{
  left: 0;
}

.drawer-close{
  font-size: 1.5rem;
  padding: 5px;
  border-right: 5px;
  right: 10px;
  border: 2px solid grey;
  color: gray;
  width: 15px;
  float: right;
  cursor: pointer;
}

.drawer-close:hover{

}
</style>