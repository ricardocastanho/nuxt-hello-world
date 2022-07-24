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
  async asyncData({ $axios }) {
    try {
      const { data } = await $axios.get('http://localhost:3001/events')
      return {
        events: data
      }
    } catch {
      error({
        statusCode: 503,
        message: 'Unable to fetch events events at this time'
      })
    }
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
