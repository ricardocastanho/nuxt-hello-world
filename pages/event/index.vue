<template>
  <div>
    <h1>Events</h1>

    <EventCard
      v-for="(event, i) in events"
      :key="i"
      :event="event"
      :data-index="i"
    />
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'EventListPage',
  asyncData(ctx) {
    return ctx.$axios.get('http://localhost:3001/events').then(response => {
      return {
        events: response.data
      }
    }).catch(() => {
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time, please try again'
      })
    })
  },
  head() {
    return {
      title: 'Events',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'What you need to know about Events'
        }
      ]
    }
  }
})
</script>
