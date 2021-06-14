<template>
  <div class="container h-100">
    <FeedbackForm />
  </div>
</template>

<script>
import FeedbackForm from "./components/FeedbackForm.vue";
export default {
  name: "App",
  components: {
    FeedbackForm,
  },
};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}
html {
  height: 100%;
}
body {
  font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}
</style>
