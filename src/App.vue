<template>
<div>
  <img src="" alt="">
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/cart">Cart</router-link>
  </div>
  <router-view/>

</div>
  
 
</template>

<script>

// import paystack from 'vue-paystack';
export default {
    components: {
        // paystack
    },
    data(){
        return{
          paystackkey: "pk_test_fd6b060ad8fce5062160139d5e1bdbd1630586ea", //paystack public key
          email: "inipayose@yahoo.com", // Customer email
          amount: 1000000 // in kobo
        }
    },
    computed: {
       cartTotal() {
      return this.$store.getters.cartTotal
      },
      reference(){
        let text = "";
        let possible = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
 
        for( let i=0; i < 10; i++ )
          text += possible.charAt(Math.floor(Math.random() * possible.length));
 
        return text;
      }
    },
    methods: {
      callback: function(response){
        console.log(response)
      },
      close: function(){
          console.log("Payment closed")
      }
    },
  mounted(){
    this.$store.commit('updateCartFromLocalStorage')
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
