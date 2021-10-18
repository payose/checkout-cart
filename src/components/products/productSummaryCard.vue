<template>
  <div class="card bg-gray-700">
    <img :src="require(`@/assets/images/${product.image}`)" alt="">
    <h3>{{ product.name }}</h3>
    <h5 class="price">Price: ${{ product.price.toFixed(2) }}</h5>
    <p class="description"> Description: {{ description }}</p>
    <p class="text-muted">{{ product.category }}</p>
    <button class="view-product" @click="$emit('view-product', product)">View</button>
  </div>
</template>

<script>
// import { mapState, mapGetters } from 'vuex'

export default {
  props: [
    'product'
  ],

  /* computed:{
   description(){
      return { this.product.description.substring(1, 4)}
   }
  } */
  computed: {
    description() {
      return this.product.description.substring(1, 5)
    }
  },

  methods: {
    view(product){
      this.$router.push({ path: `/product/${this.product.id}` })
      this.$store.dispatch('viewItem', product)
      // this.$store.dispatch('searchCategories', tabName.id)

    }
  }
}
</script>
