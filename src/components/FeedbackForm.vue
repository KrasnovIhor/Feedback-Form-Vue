<template>
  <form
    v-on:submit.prevent="submit"
    id="feedback-form"
    method="post"
    class="form-group mx-auto"
  >
    <div id="app" class="container col-sm-10 mx-auto">
      <h1 class="pt-4 mb-5">Feedback Form</h1>
      <div class="mb-4">
        <input
          type="text"
          :class="{ 'is-invalid': validationStatus($v.name) }"
          class="form-control"
          id="exampleFormControlInput1"
          placeholder="Name"
          v-model.trim="$v.name.$model"
        />
        <div v-if="!$v.name.required" class="invalid-feedback">
          Name field is required.
        </div>
      </div>
      <div class="mb-3">
        <input
          type="email"
          :class="{ 'is-invalid': validationStatus($v.email) }"
          class="form-control"
          id="exampleFormControlInput1"
          placeholder="Email"
          v-model.trim="$v.email.$model"
        />
        <div v-if="!$v.email.required" class="invalid-feedback">
          Email field is required.
        </div>
        <div v-if="!$v.email.email" class="invalid-feedback">
          Please paste correct email address.
        </div>
      </div>
      <Rating v-on:childToParent="onChildClick" />
      <!-- <div class="rating">
        <p>Rate us</p>
        <b-form-rating
          v-model="value"
          variant="warning"
          class="mb-1 rating"
          size="lg"
        ></b-form-rating>
      </div> -->
      <!-- <div class="mb-4">
        <span class="mb-4">{{ value }} of 5</span>
      </div> -->
      <div class="mb-5">
        <textarea
          :class="{ 'is-invalid': validationStatus($v.comment) }"
          class="form-control textarea"
          id="exampleFormControlTextarea1"
          rows="3"
          placeholder="Comments"
          v-model="$v.comment.$model"
        ></textarea>
        <div v-if="!$v.comment.required" class="invalid-feedback">
          Comment field is required.
        </div>
      </div>
      <button :disabled="$v.$invalid" class="btn btn-primary mb-4">
        Send Feedback
      </button>
    </div>
  </form>
</template>

<script>
import { required, email } from "vuelidate/lib/validators";
import Rating from "./Rating.vue";
export default {
  components: { Rating },
  name: "FeedbackForm",
  data: function () {
    return {
      name: "",
      email: "",
      comment: "",
      value: "0",
      fromChild: "",
    };
  },
  validations: {
    name: { required },
    email: { required, email },
    comment: { required },
  },
  methods: {
    submit: function () {
      this.$v.$touch();

      if (this.$v.$pending || this.$v.$error) return;

      console.log(Rating);

      const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          name: this.name,
          email: this.email,
          rating: this.value,
          comment: this.comment,
        }),
      };
      fetch(
        "https://it-academy-viseven.herokuapp.com/task6-check",
        requestOptions
      )
        .then((response) => response.json())
        .then((data) => console.log(data))
        .catch((error) => console.log(error));
    },
    validationStatus: function (validation) {
      return typeof validation != "undefined" ? validation.$error : false;
    },
    onChildClick(value) {
      console.log(value);
      this.fromChild = value;
    },
  },
};
</script>

<style scoped>
h1 {
  text-transform: uppercase;
  font-size: 36px;
  font-weight: 700;
  color: #303030;
}
p {
  font-size: 24px;
  font-weight: 700;
  text-transform: uppercase;
}
.pt-4 {
  padding-top: 40px !important;
}
.mb-3 {
  margin-bottom: 30px !important;
}

.mb-4 {
  margin-bottom: 40px !important;
}
.mb-5 {
  margin-bottom: 50px !important;
}
.mt-4 {
  margin-top: 40px !important;
}
.mt-5 {
  margin-top: 50px !important;
}
.form-control {
  border-radius: 10px;
  outline: none;
  border-color: #fff;
  height: 50px;
  font-size: 24px;
  padding-left: 21px;
}
.form-control.is-invalid {
  border-color: #dc3545;
}
.rating {
  border: unset;
}
.form-control-lg {
  font-size: 47px;
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

.form-control::placeholder {
  color: #303030;
  font-size: 24px;
}

.form-control.textarea {
  height: 200px;
}
.btn-primary {
  background-color: #6633ff;
  border-radius: 25px;
  font-size: 24px;
  font-weight: bold;
  padding: 0 62px;
  height: 50px;
  margin-bottom: 40px !important;
}
form {
  background-color: #f0f0f0;
  border-radius: 10px;
  width: 600px;
}
form textarea {
  resize: none;
}
</style>
