<template>
    <div>
       
       <div style ="clear:both;"></div>
       <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
       <div v-if="meetings.length == 0">
           <h3>Brak zaplanowanych spotkań</h3>
           <button>Dodaj nowe spotkanie</button>
       </div>
       <div v-else>
         <h2>Zajęcia</h2>
         <meetings-list :meetings="meetings"></meetings-list>
       </div>
       
    </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  components: {NewMeetingForm, MeetingsList},
  data() {
      return {
          meetings: [],
          add: ""
      };
  },
  methods: {
      addNewMeeting(meeting) {
          this.meetings.push(meeting);
      }
  }
}
</script>