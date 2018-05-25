<template>
   <div>
       <label id="text">Zaloguj się e-mailem</label>
       <input type="email" v-model="email">
       <span id="zaloguj">
         <button  @click="enter()"> {{ buttonLabelToDisplay }} </button>
        </span>
   </div>
</template>

<script>
export default {
  props: ["buttonLabel"],
  computed: {
    buttonLabelToDisplay() {
      return this.buttonLabel || "Zaloguj się";
    }
  },
  data() {
    return {
      email: ""
      
    };
  },
  methods: {
    enter() {
      this.$emit("login", this.email);
    },
  }
};
</script>

<style lang="scss">
#text{

  text-align: left;

}
#zaloguj{
  float:left;
  
}


</style>