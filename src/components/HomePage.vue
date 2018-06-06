<template>
    <div class="container">
      <div class="row">
          <div class="column">
              <h3>Witaj {{ email }}!</h3>
          </div>
          <div class="column">
              <button class="button button-outline" @click="signOut()">Wyloguj</button>
          </div>
      </div>

      <div class="row">
          <div class="column">
              <meeting-page :email="email"></meeting-page>
          </div>
      </div>
    </div>
</template>

<script>
import MeetingPage from './meetings/MeetingPage.vue';

export default {
props: ['email'],
components: {
    MeetingPage
},
methods: {
    signOut() {
        this.$emit('signOut');
    }
}
}
</script>

<style>

</style>
