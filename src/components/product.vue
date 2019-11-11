<template>
  <div class="card my-5">
    <div class="card-header">
      <h5 class="text-center card-title">{{product.name}}</h5>
    </div>
    <div class="card-body">
        <div class="card-image d-flex justify-content-center">
            <img :src="product.image" alt="product.price" :key="product.id">
        </div>
      <p class="text-center text-muted card-text display-4">${{product.price}}</p>
      <button :disabled="isInCart" @click="$emit('add-to-cart',product)" class="btn btn-primary form-control">
          {{ isInCart? 'Added To Cart' : 'Add To Card' }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product","isInCart"]
};
</script>