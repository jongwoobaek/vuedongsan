<template>
  <div class="black-bg" v-if="isOpen">
    <div class="white-bg">
      <h4>상세 페이지</h4>
      <p>상세 페이지 내용</p>
      <button @click="closeModal">모달 닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductModal",
  props: {
    isOpen: Boolean,
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
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
</style>
