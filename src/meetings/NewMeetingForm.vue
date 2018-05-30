<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <button onsubmit="return addNewMeeting()">Dodaj</button>
            
            <div v-if="isNazwaEmpty">
            <label id="emptyNameLabel">Spotkanie musi posiadać nazwę!</label>
            </div>
            <div style="clear:both;"></div>
            <div v-if="this.counter==0">
                <h3>Brak zaplanowanych spotkań</h3>
            </div>
            <div v-else>
            <h3>Zaplanowane Zajęcia ({{counter}}) </h3>
            </div>
            
    </form>
</template>

<script>
export default {
  data() {
    return {
      newMeeting: {},
      isNazwaEmpty: false,
      counter: 0
    };
  },
  methods: {
    addNewMeeting() {
      if (!this.newMeeting.name) {
        this.isNazwaEmpty = true;
      } else {
        this.$emit("added", this.newMeeting);
        this.newMeeting = {};
        this.isNazwaEmpty = false;
        this.counter++;
      }
    }
  }
};
</script>

<style>
#emptyNameLabel {
  color: red;
  float: left;
  margin-left: 20px;
}

label {
  text-align: left;
}

button {
  float: left;
}
</style>
