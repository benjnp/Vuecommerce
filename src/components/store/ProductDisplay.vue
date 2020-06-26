<template>
  <div>
    <h3>Products</h3>
    
    <v-row>
      <v-col
        sm="6"
        md="4"
        v-for="product in filteredProducts"
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
  data() {
    return {
      filteredProducts: []
    };
  },
  components: {
    VerticalProduct
  },
  computed: {
    ...mapState([
      "products",
      "filter",
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
    // filter() {
    //   //const allowed = 50;
    //   let filtered = this.products.filter(prod => prod.price > this.filter);

    //   // const filtered = Object.keys(this.products.price)
    //   // .filter(key => allowed.includes(key))
    //   // .reduce((obj, key) => {
    //   //   obj[key] = raw[key];
    //   //   return obj;
    //   // }, {});

    //   console.log(filtered);
    // }
  },
  created() {
    switch (this.filter) {
      case 0:
        this.filteredProducts = this.products;
        break;
      case 1:
        this.filteredProducts = this.products.filter(prod => prod.price < 25);
        break;
      case 2:
        this.filteredProducts = this.products.filter(
          prod => prod.price > 24 && prod.price < 101
        );
        break;
      case 3:
        this.filteredProducts = this.products.filter(
          prod => prod.price > 99 && prod.price < 501
        );
        break;
      case 4:
        this.filteredProducts = this.products.filter(prod => prod.price > 499);
        break;
    }
  }
};
</script>
