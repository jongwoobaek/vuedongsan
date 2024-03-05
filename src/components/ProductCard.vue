<template>
  <div>
    <img :src="product.image" alt="room image" class="room-img" />
    <h4 @click="openModal">{{ product.title }}</h4>
    <p>{{ product.price }} 원</p>
    <button @click="likeIncrease(product)">좋아요</button>
    <span>좋아요 수 : {{ product.likeNum }}</span>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: {
    product: Object,
  },
  methods: {
    likeIncrease(product) {
      product.likeNum++;
    },
    openModal() {
      this.$emit("open");
    },
  },
};
</script>

<style scoped>
.room-img {
  margin-top: 40px;
  width: 100%;
}
</style>
