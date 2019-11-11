<template>
  <div class="container text-center">
    <ul class="list-group">
      <li class="list-group-item" v-for="item in items" :key="item.id">
        {{ item.name }} - ${{ item.price }}
        <button
          @click="$emit('remove-from-cart', item)"
          class="btn badge btn-danger float-right"
        >Remove From Cart</button>
      </li>
    </ul>
    <div class="card p-3 mt-2">
      <h4 class="text-center">${{ total }}</h4>
    </div>

    <button :disabled="items.length===0" @click="$emit('payNow')" class="btn btn-success">Pay Now</button>
  </div>
</template>

<script>
export default {
  props: ["items"],
  computed: {
    total() {
      return this.items.reduce((acc, item) => acc + Number(item.price), 0);
    }
  }
};
</script>