<template>
  <ProductModal
    :isOpen="isOpenModal"
    :product="selectedProduct"
    @close="isOpenModal = false"
  />

  <div class="menu">
    <a v-for="(menu, index) in menuList" :key="index">{{ menu }}</a>
  </div>

  <h1 :style="blueText">Vuedongsan</h1>
  <div v-for="product in products" :key="product.id">
    <img :src="product.image" alt="room image" class="room-img" />
    <h4 v-on:click="openModal(product)">{{ product.title }}</h4>
    <p>{{ product.price }} 원</p>
    <button v-on:click="likeIncrease(product)">좋아요</button>
    <span>좋아요 수 : {{ product.likeNum }}</span>
  </div>
</template>

<script>
import ProductModal from "./components/ProductModal";
import productList from "./assets/productList";

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
    likeIncrease(product) {
      product.likeNum++;
    },
    openModal(product) {
      this.isOpenModal = true;
      this.selectedProduct = product;
    },
  },
  components: {
    ProductModal,
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

.room-img {
  margin-top: 40px;
  width: 100%;
}
</style>
./assets/productList
