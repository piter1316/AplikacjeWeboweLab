<template>
    <div>
    <button @click="showMeetingForm = !showMeetingForm" style="text-transform: uppercase;">Dodaj nowe spotkanie</button>
       <new-meeting-form v-if="showMeetingForm" @added="addNewMeeting($event)"></new-meeting-form>
       <meetings-list @signOutMeeting="signOutMeeting($event)" @removeMeeting="removeMeeting($event)" @signToMeeting="signToMeeting($event)" :meetings="meetings" :email="email"></meetings-list>
    </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  components: { NewMeetingForm, MeetingsList },
  props: ["email"],
  data() {
    return {
      meetings: [],
      showMeetingForm: false
    };
  },
  methods: {
    addNewMeeting(meeting) {
      this.showMeetingForm = false;
      this.meetings.push(meeting);
    },
    signToMeeting(meeting) {
      if (!meeting.participants) {
        meeting.participants = [];
      }

      meeting.participants.push(this.email);

      this.meetings = this.meetings.filter(m => m.name !== meeting.name);
      this.meetings.push(meeting);
    },
    signOutMeeting(meeting) {
      meeting.participants = meeting.participants.filter(p => p !== this.email);

      this.meetings = this.meetings.filter(m => m.name !== meeting.name);
      this.meetings.push(meeting);
    },
    removeMeeting(meeting) {
      this.meetings = this.meetings.filter(m => m.name !== meeting.name);
    }
  }
};
</script>