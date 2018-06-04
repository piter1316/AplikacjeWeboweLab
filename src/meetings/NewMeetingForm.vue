<template>
  
    <form @submit.prevent="addNewMeeting()">
            <div v-if="show">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <button >Dodaj</button>
            </div>
            
            <div v-if="isNazwaEmpty">
            <label id="emptyNameLabel">Spotkanie musi posiadać nazwę!</label>
            </div>
            <div style="clear:both;"></div>
            <div v-if="this.counter==0">
                <h3>Brak zaplanowanych spotkań</h3>
            </div>
            <div v-else>
            <h3>Zaplanowane Zajęcia ({{counter}}) </h3>
            <div v-if="show==false">
            <button @click="showForm()">Dodaj Nowe Zajęcia&&&</button>
            </div>
            </div>
              
    </form>
  
</template>

<script>
export default {
  data() {
    return {
      newMeeting: {},
      isNazwaEmpty: false,
      counter: 0,
      show: true
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
        this.show = false;
      }
    },
    showForm(){
      this.show = true;
      this.isNazwaEmpty = false;
      
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
