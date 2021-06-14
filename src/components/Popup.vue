<template>
  <div class="popup">
    <div class="popup-inner">
      <slot />
      <button @click="emitToClose" class="popup-close btn-primary mt-5">
        OK
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    emitToClose() {
      this.$emit("closeModal");
    },
  },
};
</script>

<style lang="scss" scoped>
.popup {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 99;
  background-color: rgba(0, 0, 0, 0.2);
  display: flex;
  justify-content: center;
  align-items: center;
  .popup-inner {
    background: #f0f0f0;
    border-radius: 10px;
    height: 300px;
    width: 600px;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
}
</style>