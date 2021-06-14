<template>
  <div class="container h-100">
    <FeedbackForm />
  </div>
  <!-- <form action="" class="mx-auto">
    <div id="app" class="container col-sm-10 mx-auto">
      <h1 class="pt-4 mb-5">Feedback Form</h1>
      <div class="mb-4">
        <input
          type="text"
          class="form-control"
          id="exampleFormControlInput1"
          placeholder="Name"
          v-model.trim="name"
        />
      </div>
      <div class="mb-4">
        <input
          type="email"
          class="form-control"
          id="exampleFormControlInput1"
          placeholder="Email"
          v-model.trim="email"
        />
      </div>
      <div class="mb-5">
        <textarea
          class="form-control textarea"
          id="exampleFormControlTextarea1"
          rows="3"
          placeholder="Comments"
          v-model="comment"
        ></textarea>
      </div>
      <button type="submit" class="btn btn-primary mb-4">Send Feedback</button>
    </div>
  </form> -->
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
