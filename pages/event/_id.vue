<template>
  <div>
    <h1>{{ event.title }}</h1>
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'EventShowPage',
  async asyncData({ $axios, error, params }) {
    try {
      const { data } = await $axios.get(
        'http://localhost:3001/events/' + params.id
      )
      return {
        event: data
      }
    } catch {
      error({
        statusCode: 503,
        message: 'Unable to fetch event #' + params.id
      })
    }
  },
  head() {
    return {
      title: 'Event #' + this.id,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'What you need to know about Event #' + this.id
        }
      ]
    }
  },
  computed: {
    id() {
      return this.$route.params.id
    }
  }
})
</script>
