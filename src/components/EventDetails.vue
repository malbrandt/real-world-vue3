<template>
  <div v-if="event">
    <span>Event #{{ id }}</span>
    <h1>{{ event.title }}</h1>
  </div>
</template>

<script>
import EventService from '@/services/EventService'

export default {
  props: ['id'],
  data() {
    return {
      event: null
    }
  },
  created() {
    EventService.getEvent(this.id)
      .then(response => {
        this.event = response.data
      })
      .catch(err => console.log(err))
  }
}
</script>
