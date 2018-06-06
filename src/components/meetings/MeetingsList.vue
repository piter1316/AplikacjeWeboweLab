<template>
<div>
    <div v-if="meetings && meetings.length > 0">
        <h3>Zaplanowane spotkania ({{ meetings.length }})</h3>
    <table v-if="meetings.length > 0">
        <thead>
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <td>{{ meeting.name }}</td>
                <td>{{ meeting.description }}</td>
                <td>
                    <span v-for="part in meeting.participants" :key="part"> {{ part }} </span>
                </td>
                <td>
                    <button v-if="!isInMeeting(meeting)" @click="signToMeeting(meeting)" style="text-transform: uppercase; margin-right: 5px;" class="button button-outline">Zapisz się</button>
                    <button v-else @click="signOutMeeting(meeting)" style="text-transform: uppercase; margin-right: 5px;" class="button button-outline">Wypisz się</button>
                    <button v-if="meeting.participants && meeting.participants.length < 1 || !meeting.participants" @click="removeMeeting(meeting)" style="text-transform: uppercase;">Usuń puste spotkanie</button>
                </td>
            </tr>
        </tbody>
    </table>
    </div>
    <div v-else>
        <h4>Brak zaplanowanych spotkań</h4>
    </div>
</div>
</template>

<script>
export default {
  props: ["meetings", "email"],
  methods: {
    signToMeeting(meeting) {
      this.$emit("signToMeeting", meeting);
      this.isInMeeting(meeting);
    },
    signOutMeeting(meeting) {
      this.$emit("signOutMeeting", meeting);
      this.isInMeeting(meeting);
    },
    removeMeeting(meeting) {
      this.$emit("removeMeeting", meeting);
    },
    isInMeeting(meeting) {
      if (meeting.participants) {
        return !(meeting.participants.indexOf(this.email) < 0);
      }

      return false;
    }
  }
};
</script>