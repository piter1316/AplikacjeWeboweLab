<template>
<div>
    
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

                <td></td>

                <td><button  v-on:click.stop="addUser()"> ZAPISZ SIĘ</button></td>
                <td><button> USUŃ PUSTE SPOTKANIE</button></td>
            </tr>
        </tbody>
    </table>
</div>
</template>

<script>
export default {
  
  props: ["meetings"],

  data() {
    return { 
        counter: 0};
  },
  methods: {
    addUser() {
      this.user = email;
    },
    counter(){
        return this.counter;

    }
  }
};
</script>

<style>
h3{
    text-align: left;
}
</style>