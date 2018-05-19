<template>
  <div id="app">
    <!-- <h1>Twój e-mail to: {{ email}}</h1>
    <div v-if="email.length < 10">Ale masz krótki adres!</div>
    <div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
    <div v-else>Twój adres e-mail jest stanowczo za długi.</div>
    <input type="email" v-model="email">
    <button @click="alertMyEmail()">Wyświetl mój e-mail w alercie</button> -->

    <h1>{{ welcome}}</h1>
    <div v-if="!state">
      <label>Zaloguj się mailem</label>
      <input type="email" v-model="email">
      <button @click="login()"> Wchodzę</button>
    </div>
     <div v-else>
       <label>zalogowany jako {{email}}</label>
        <button @click="logout()">Wyloguj </button>

     </div>

    
  </div>
</template>

<script>
import "milligram";
export default {
  name: 'app',
  data () {
    return {
      email: 'piotrek@poczta.pl',
      welcome: 'Witaj w systemie do zapisów na zajęcia',
      state: false,
    }
  },
  methods: {
  alertMyEmail() {
    alert(this.email);
  },
  login(){
    
      this.state = true
  },
  logout(){

    this.state = false
  }
}

}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
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
