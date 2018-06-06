<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <button>Dodaj</button><span v-if="showValidationError" style="color: red; font-weight: bold; margin-left: 5px;">Spotkanie musi mieć nazwę!</span>
        </form>
</template>

<script>
export default {
  data() {
      return {
          showValidationError: false,
          newMeeting: {}
      };
  },
  methods: {
      addNewMeeting() {
          if (!this.newMeeting.name) {
              this.showValidationError = true;
              return;
          }

        this.$emit('added', this.newMeeting);
        this.newMeeting = {};
    }
  }
}
</script>