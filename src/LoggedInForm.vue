
<template>
   <form>
     
     <div style="background:black;">
       <h2>Witaj  {{ nameToDisplay }}!</h2>
       <button id="wyloguj" @click="exit()">Wyloguj </button>
      
     </div>
     
     <div style="clear: both"></div>
   </form>
   
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

<style>
#wyloguj {
  float: right;
  align-self: right;
}
h2 {
  float: left;
}
</style>