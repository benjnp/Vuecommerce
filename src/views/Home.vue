<template>
  <div>
    <Header />
    <PopularProducts />
    <Footer />
  </div>
</template>

<script>
import Header from "../components/home/Header";
import PopularProducts from "../components/home/PopularProducts";
import Footer from "../components/home/Footer";

export default {
  components: {
    Header,
    PopularProducts,
    Footer
  }
};
</script>
