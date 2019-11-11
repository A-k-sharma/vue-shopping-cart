<template>
  <div class="container">
    <div class="row">
      <div class="col-md-7">
		  <div class="row">
			  <div  :key="product.id" class="col-md-6" v-for="product in products">
				  <product :isInCart="isInCart(product)" v-on:add-to-cart="addToCart(product)" :product="product"></product>
			  </div>
		  </div>
	  </div>
      <div class="col-md-5 mt-5">
		  <cart v-on:payNow="payNow()" v-on:remove-from-cart="removeFromCart($event)" :items="cart">

		  </cart>
	  </div>
    </div>
  </div>
</template>

<script>
import products from '/home/ttn/Documents/first-vue-app/src/products.json'
import Product from './components/product.vue';
import Cart from './components/cart.vue';

export default {
  name: "app",
  components:{
	  Product,
	  Cart
  },
  data() {
	  return {
		  products,
		  cart: []
	  }
  },
  methods:{
	  addToCart(product){
		  this.cart.push(product)
	  },
	  isInCart(product){
		  const item = this.cart.find( item => item.id == product.id )
		  if(item){
		  	return true
		  }
		  else{
			  return false
		  }
	  },
	  removeFromCart(product){
		  this.cart= this.cart.filter(item=> item.id !== product.id); 
	  },
	  payNow(){
		  
		  this.cart = [];
		  alert("Thank You For Buying!!!! See You Soon Again");
	  }
  }
};
</script>

<style lang="scss">
body {
  background-color: antiquewhite;
}
</style>
