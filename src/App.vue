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

  <button @click="sortByPriceAsc">가격 낮은 순 정렬</button>
  <button @click="sortByPriceDesc">가격 높은 순 정렬</button>
  <button @click="sortByName">이름 순으로 정렬</button>
  <button @click="displayLowPriceProducts">저가 상품 보기</button>
  <button @click="resetSort">되돌리기</button>

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
      originProducts: [...productList],
      menuList: ["Home", "Shop", "About"],
    };
  },
  methods: {
    openModal(product) {
      this.isOpenModal = true;
      this.selectedProduct = product;
    },
    sortByPriceAsc() {
      this.products.sort(
        (product1, product2) => product1.price - product2.price
      );
    },
    sortByPriceDesc() {
      this.products.sort(
        (product1, product2) => product2.price - product1.price
      );
    },
    sortByName() {
      this.products.sort((product1, product2) => {
        const titleA = product1.title.toLowerCase();
        const titleB = product2.title.toLowerCase();

        if (titleA < titleB) {
          return -1;
        } else if (titleA > titleB) {
          return 1;
        } else {
          return 0;
        }
      });
    },
    displayLowPriceProducts() {
      this.products = this.originProducts.filter(
        (product) => product.price <= 500000
      );
    },
    resetSort() {
      this.products = [...this.originProducts];
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
