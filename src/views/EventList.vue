<template>
  <div>
    <h1>Event Listing</h1>
    <EventCard v-for="(event, idx) in events" :key="idx" :event="event"/>
  </div>
</template>

<script>
  import EventCard from '@/components/EventCard.vue';
  import EventService from '@/services/EventService.js'

  export default {
    components: {
      EventCard
    },
    data() {
      return {
        events: []
      }
    },
    created() {
      EventService.getEvents()
      .then(data => this.events = data.data)
      .catch(error => console.log(error.response))
    }
  }
</script>

<style lang="css" scoped>
</style>
