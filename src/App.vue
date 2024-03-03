<template>
  <div class="menu">
    <a v-for="(menu, index) in menuList" :key="index">{{ menu }}</a>
  </div>

  <div>
    <h1 :style="blueText">Vuedongsan</h1>
    <h4>{{ products[0] }}</h4>
    <p>{{ price1 }} 만원</p>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>{{ price2 }} 만원</p>
  </div>
  <div>
    <h4>{{ products[2] }}</h4>
    <p>{{ price2 }} 만원</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      price1: 60,
      price2: 70,
      blueText: "color: blue",
      products: ["역삼동 원룸", "천호동 원룸", "마포구 원룸"],
      menuList: ["Home", "Shop", "About"],
    };
  },
  components: {},
};
</script>

<style>
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
</style>
