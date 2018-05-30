<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <button onsubmit="return addNewMeeting()">Dodaj</button>
            
            <div v-if="isNazwaEmpty">
            <label id="emptyNameLabel">SPOTKANIE MUSI MIEĆ NAZWĘ</label>
            </div>
            <div style="clear:both;"></div>
            <h3>Zajęcia ({{counter}}) </h3>
            
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
      }
      else {
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
#emptyNameLabel{
    color:red;
    float:left;
    margin-left: 20px;
}

label{
    text-align: left;
    
}

button{
    float: left;
}
</style>
