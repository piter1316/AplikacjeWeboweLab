<template>
  <div id="app">
    <!-- <h1>Twój e-mail to: {{ email}}</h1>
    <div v-if="email.length < 10">Ale masz krótki adres!</div>
    <div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
    <div v-else>Twój adres e-mail jest stanowczo za długi.</div>
    <input type="email" v-model="email">
    <button @click="alertMyEmail()">Wyświetl mój e-mail w alercie</button> -->

    <h1>{{ welcome}}</h1>
    <div v-if="!authenticatedUsername">
      <login-form @login="logMeIn($event)" :button-label="'Wejdź'"></login-form>
      <login-form @login="logMeIn($event)" :button-label="'WLEĆ'"></login-form>
      <login-form @login="logMeIn($event)" :button-label="'Zaloguj się jako człowiek'"></login-form>
      <login-form @login="logMeIn($event)" ></login-form>

    </div>
     <div v-else>
        <logged-in-form @logout="logout($event)" :authenticatedUsername = this.authenticatedUsername></logged-in-form>
     </div>
    
    
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import LoggedInForm from "./LoggedInForm";
export default {
  name: "app",
  components: { LoginForm, LoggedInForm },
  data() {
    return {
      email: "piotrek@poczta.pl",
      welcome: "Witaj w systemie do zapisów na zajęcia",
      authenticatedUsername: "",
      state: false
    };
  },
  methods: {
    alertMyEmail() {
      alert(this.email);
    },
    logMeIn(username) {
      this.authenticatedUsername = username;
    },
    logout() {
      this.authenticatedUsername = "";
    },
    getUserName(){
      return authenticatedUsername;
    }
  }
};











</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
