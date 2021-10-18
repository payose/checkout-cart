<template>
  <div class="home">
    <productDescription
      :product = "product"
      :active = "active.productViewer"
      v-on:close-product-drawer="closeProductDrawer()"
    />  
          
    <div class="product-card-contai">
      <productSummaryCard
        v-for="product in items"
        :key ="product.id"
        :product = product 
        v-on:view-product="viewProduct($event)"
        />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import items from '@/data/items.js'
import productSummaryCard from '@/components/products/productSummaryCard.vue'
import productDescription from '@/components/products/productDescription.vue'

export default {
  name: 'Home',
  components: {
    productSummaryCard,
    productDescription,
  },

  data () {
    return {
      items : items,
      product: null,
      active: {
        productViewer:false
      }
    }
  },

  methods: {
    viewProduct(product) {
      this.product = product
      // this.$router.push({ path: `/product/${this.product.id}` })
      this.$store.state.viewedItem = this.product

      this.active.productViewer = true
    },

     closeProductDrawer() {
       this.active.productViewer =false
     }
  }
}
</script>
