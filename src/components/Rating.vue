<template>
  <div class="rating">
    <p>Rate us</p>
    <b-form-rating
      @change="emitToParent"
      v-model="value"
      variant="warning"
      class="mb-1 rating"
      size="lg"
    ></b-form-rating>
    <div class="mb-4">
      <span class="mb-4">{{ value }} of 5</span>
    </div>
  </div>
</template>
<script>
export default {
  name: "Rating",
  data: () => {
    return {
      value: "0",
    };
  },
  methods: {
    emitToParent() {
      this.$emit("childToParent", this.value);
    },
  },
};
</script>

<style>
.rating {
  border: unset;
}
.rating svg {
  width: 50px !important;
  height: 47px !important;
}
.b-rating {
  background: transparent;
}
.b-rating-star {
  font-size: 48px;
}
svg {
  width: 50px !important;
  height: 47px !important;
  cursor: pointer;
}
</style>
