<template>
  <div>
    <h1>Events</h1>

    <div v-for="i in 5" :key="i">
      <NuxtLink :to="`/event/${i}`">
        Event #{{ i }}
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  name: 'EventListPage',
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
}
</script>
