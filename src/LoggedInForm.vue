
<template>
   <div>
     <label>zalogowany jako {{ nameToDisplay }}</label>
     <button @click="exit()">Wyloguj </button>
   </div>
</template>


<script>
export default {
  props: ["authenticatedUsername"],
  computed: {
    nameToDisplay() {
      return this.authenticatedUsername || "USER";
    }
  },

  data() {
    return {
      authenticatedUsername: this.authenticatedUsername
    };
  },
  methods: {
    exit() {
      this.$emit("logout", this.authenticatedUsername);
    }
  }
};
</script>