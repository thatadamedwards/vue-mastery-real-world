<template>
  <div>
    <h1>Events Listing</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <BaseIcon />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
import EventInteractor from '@/services/EventInteractor'

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
    EventInteractor.findEvents().then(response => {
      this.events = response.data
    })
  }
}
</script>

<style lang="scss" scoped></style>
