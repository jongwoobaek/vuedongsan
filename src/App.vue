<template>
  <ProductModal :isOpen="isOpenModal" @close="isOpenModal = false" />

  <div class="menu">
    <a v-for="(menu, index) in menuList" :key="index">{{ menu }}</a>
  </div>

  <h1 :style="blueText">Vuedongsan</h1>
  <div v-for="(product, index) in products" :key="index">
    <img :src="getImageSrc(index)" alt="room image" class="room-img" />
    <h4 v-on:click="isOpenModal = true">{{ product.name }}</h4>
    <p>{{ product.price }} 만원</p>
    <button v-on:click="reportIncrease(product)">허위 매물 신고</button>
    <span>신고 수 : {{ product.num }}</span>
  </div>
</template>

<script>
import ProductModal from "./components/ProductModal";

export default {
  name: "App",
  data() {
    return {
      isOpenModal: false,
      blueText: "color: blue",
      products: [
        {
          name: "역삼동 원룸",
          price: 60,
          num: 0,
        },
        {
          name: "천호동 원룸",
          price: 70,
          num: 0,
        },
        {
          name: "마포구 원룸",
          price: 80,
          num: 0,
        },
      ],
      menuList: ["Home", "Shop", "About"],
    };
  },
  methods: {
    reportIncrease(product) {
      product.num++;
    },
    getImageSrc(index) {
      return require(`./assets/rooms/room${index}.jpg`);
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
