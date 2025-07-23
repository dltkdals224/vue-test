<template>
  <form action="" @submit.prevent="handleSubmit">
    <div>
      <label for="email">email:</label>
      <input id="email" type="text" v-model="email" />
    </div>
    <div>
      <label for="password">password:</label>
      <input type="password" v-model="password" />
    </div>
    <button type="submit">로그인</button>
  </form>
</template>

<script>
import axios from "axios";
import { ref } from "vue";

export default {
  name: "App",
  setup() {
    // data
    const email = ref("");
    const password = ref("");

    // methods
    const handleSubmit = () => {
      axios
        .post("https://jsonplaceholder.typicode.com/users/", {
          email: email.value, // composition api 특징
          password: password.value,
        })
        .then((res) => {
          console.log(res);
        });
    };

    return { email, password, handleSubmit }; // <template> 표현식에서 사용 가능
  },
};
</script>
