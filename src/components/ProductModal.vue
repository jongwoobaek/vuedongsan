<template>
  <div class="black-bg" v-if="isOpen">
    <div class="white-bg">
      <img :src="product.image" alt="" />
      <h4>{{ product.title }}</h4>
      <p>{{ product.content }}</p>
      <p>{{ product.price }} 원</p>
      <DiscountBanner />
      <button @click="closeModal">모달 닫기</button>
    </div>
  </div>
</template>

<script>
import DiscountBanner from "./DiscountBanner";

export default {
  name: "ProductModal",
  props: {
    isOpen: Boolean,
    product: Object,
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
  components: {
    DiscountBanner,
  },
};
</script>

<style scoped>
.black-bg {
  padding: 20px;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
}

.white-bg {
  border-radius: 8px;
  padding: 20px;
  width: 100%;
  background-color: white;
}

img {
  width: 80%;
}
</style>
