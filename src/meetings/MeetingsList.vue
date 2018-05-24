<template>
    <table v-if="meetings.length > 0">
        <thead>
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
                <th></th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <td>{{ meeting.name }}</td>
                <td>{{ meeting.description }}</td>
                <td>{{ user }}</td>
                <td><button  v-on:click.stop="addUser()"> ZAPISZ SIĘ</button></td>
                <td><button> USUŃ PUSTE SPOTKANIE</button></td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
  props: ["meetings"],
  data() {
    return {user : ""}
  },
  methods:{
      addUser(){
          this.user = 'dodany'

      }
  }
};
</script>