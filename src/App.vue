<template>
  <Transition name="fade">
    <ProductModal
      :isOpen="isOpenModal"
      :product="selectedProduct"
      @close="isOpenModal = false"
    />
  </Transition>

  <div class="menu">
    <a v-for="(menu, index) in menuList" :key="index">{{ menu }}</a>
  </div>

  <h1 :style="blueText">Vuedongsan</h1>

  <DiscountBanner />

  <ProductCard
    v-for="product in products"
    :key="product.id"
    :product="product"
    @open="openModal(product)"
  />
</template>

<script>
import ProductModal from "./components/ProductModal";
import productList from "./assets/productList";
import DiscountBanner from "./components/DiscountBanner";
import ProductCard from "./components/ProductCard";

export default {
  name: "App",
  data() {
    return {
      isOpenModal: false,
      blueText: "color: blue",
      products: productList,
      selectedProduct: null,
      menuList: ["Home", "Shop", "About"],
    };
  },
  methods: {
    openModal(product) {
      this.isOpenModal = true;
      this.selectedProduct = product;
    },
  },
  components: {
    ProductModal,
    DiscountBanner,
    ProductCard,
  },
};
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  border-radius: 5px;
  padding: 15px;
  background-color: darkslateblue;
}

.menu a {
  padding: 10px;
  color: white;
  text-decoration: none;
}

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 0.75s;
}

.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 0.75s;
}

.fade-leave-to {
  opacity: 0;
}
</style>
