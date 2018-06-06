<template>
  <div class="container">
      <div class="row">
        <div class="column">
        <h1>System zapisów na zajęcia</h1>
        <login-form v-show="!isLoggedIn" @signIn="signIn($event)"></login-form>
        <home-page :email="email" @signOut="signOut($event)" v-show="isLoggedIn"></home-page>
        </div>
      </div>
    </div>
</template>
<script>
import HomePage from "./HomePage.vue";
import LoginForm from "./LoginForm.vue";

export default {
  components: {
    LoginForm,
    HomePage
  },
  data() {
    return {
      email: '',
      isLoggedIn: false
    };
  },
  methods: {
    signIn(email) {
      this.isLoggedIn = true;
      this.email = email;
    },
    signOut() {
      this.isLoggedIn = false;
      this.email = ''
    }
  }
};
</script>

<style>
</style>
