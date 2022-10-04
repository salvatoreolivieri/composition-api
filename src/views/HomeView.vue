<template>
  <main>
    <h1>{{ shopName }}</h1>

    <YummyMeal
      v-for="item in meals"
      :name="item.name"
      :price="item.price"
      @addToCart="addItemToCart"
    />
  </main>
</template>

<script>
// import
import { ref, reactive, watch } from "vue";
import YummyMeal from "../components/YummyMeal.vue";

// export
export default {
  setup() {
    // Variable
    const shopName = ref("Yummy Meals Shop!");

    const meals = reactive([
      { name: "Hamburger", price: 8 },
      { name: "Cheeseburger", price: 6 },
      { name: "Carrot", price: 1 },
      { name: "Chips", price: 2 },
    ]);

    const cart = reactive([]);

    // Function
    const addItemToCart = (item) => cart.push(item);

    watch([() => [...cart]], (newValue, oldValue) =>
      console.log(newValue, oldValue)
    );

    // Return
    return { addItemToCart, shopName, meals };
  },

  // Components
  components: { YummyMeal },
};
</script>
