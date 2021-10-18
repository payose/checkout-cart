<template>
  <div>
   <ProductDetails/>
   <h1>{{viewedItem}}</h1>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import ProductDetails from '../components/products/productDetails.vue'
export default {
  computed: {
    ...mapState([
      'viewedItem',
    ])
  },
 components:{
   ProductDetails
 }
}
</script>

