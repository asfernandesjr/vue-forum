<template>
  <div class="col-full">
    <div class="col-full push-top">
      <div class="forum-header">
        <div class="forum-details">
          <h1>{{ forum.name }}</h1>
          <p class="text-lead">
            {{ forum.description }}
          </p>
        </div>
        <router-link
          :to="{ name: 'ThreadCreate', params: { forumId: id }}"
          class="btn-green btn-small"
        >
          Start a thread
        </router-link>
      </div>
    </div>
    <div class="col-full">
      <ThreadList :threads="threads" />
    </div>
  </div>
</template>

<script>
import sourceData from '@/data.json'
import ThreadList from '@/components/ThreadList'

export default {
  components: {
    ThreadList
  },
  props: {
    id: {
      required: true,
      type: String
    }
  },
  computed: {
    forum() {
      return sourceData.forums.find(forum => forum.id === this.id)
    },
    threads() {
      return sourceData.threads.filter(thread => thread.forumId === this.id)
    }
  }
}
</script>

<style scoped>
  
</style>