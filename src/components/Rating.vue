<template>
  <div class="rating">
    <p>Rate us</p>
    <b-form-rating
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
};
</script>

<style scoped>
.rating {
  border: unset;
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
}
</style>