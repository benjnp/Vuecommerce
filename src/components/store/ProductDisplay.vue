<template>
  <div>
    <h3>Products</h3>
    
    <v-row>
      <v-col
        sm="6"
        md="4"
        v-for="product in products"
        :key="product.name"
      >
        <VerticalProduct :product="product" :addToCart="addToCart" />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import VerticalProduct from "../cards/VerticalProduct";
import { mapState } from "vuex";

export default {
  components: {
    VerticalProduct
  },
  computed: {
    ...mapState([
      "products",
      "snackbar",
      "cart",
      "addItemToCart",
      "updateSnackbar"
    ])
  },
  methods: {
    addToCart(index, quantity = 1) {
      this.$store.commit("addItemToCart", { itemId: index, quantity });
      this.$store.commit("updateSnackbar", { show: true });
    }
  }
};
</script>
