<template>
    <div>
       
       <div style ="clear:both;"></div>
       <form @submit.prevent="showAddForm()">
         <div v-if="add==true">
           <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
           <meetings-list :meetings="meetings"></meetings-list>
         </div>
        <div v-if="meetings.length == 0 && add==false">
            <h3>Brak zaplanowanych spotkań</h3>
            <button @click = "showAddForm()">Dodaj nowe spotkanie</button>
        </div>
       
         
      
       </form>
       
    </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  components: { NewMeetingForm, MeetingsList },
  data() {
    return {
      meetings: [],
      add: false
    };
  },
  methods: {
    addNewMeeting(meeting) {
      this.meetings.push(meeting);
    },
    showAddForm() {
      this.add = true;
    }
  }
};
</script>

<style>
h3{
    text-align: left;
}
button{
    float:left;
}
</style>
