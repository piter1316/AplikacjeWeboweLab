<template>
<div>
    <h2>Zaloguj sie e-mailem</h2>
    <input type="text" v-model="email">
    <button @click="signIn()">Zaloguj się</button>  
</div>
</template>

<script>
export default {
  data() {
    return {
      email: ""
    };
  },
  methods: {
    signIn() {
      this.$emit('signIn', this.email);
    }
  }
};
</script>

<style>
</style>
