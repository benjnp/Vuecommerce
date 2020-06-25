<template>
  <div>
    <v-row
      v-for="product in products"
      :key="product.name"
    >
      <HorizontalProduct
        :product="product"
        btnAction="remove"
      />
    </v-row>
  </div>
</template>

<script>
import HorizontalProduct from "../cards/HorizontalProduct";
import { mapState } from "vuex";

export default {
  components: {
    HorizontalProduct
  },
  methods: {
    removeFromCart() {}
  },
  computed: {
    ...mapState(["products"])
  }
};
</script>
