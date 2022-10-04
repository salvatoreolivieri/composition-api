<template>
  <div class="menu-item">
    <h2>{{ name }}</h2>
    <strong>{{ returnPrice }}</strong
    ><br />
    <button @click="addToCart">Add to cart</button>
  </div>
</template>

<script>
// import
import { computed } from "vue";

// export
export default {
  // Props
  props: {
    name: String,
    price: Number,
  },

  setup(props, { emit }) {
    // Function
    const addToCart = () => emit("addToCart", props.name);
    const returnPrice = computed(() => `€ ${props.price.toFixed(2)}`);

    // Return
    return { addToCart, returnPrice };
  },
};
</script>

<style scoped>
.menu-item {
  margin-bottom: 10px;
}
</style>
