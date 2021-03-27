<template>
  <div>This is the home page</div>
  <div v-for="thread in threads" :key="thread.id">
      <h2>{{ thread.title }}</h2>
      <div v-for="postId in thread.posts" :key="postId">
          <p><b>{{ userById(postById(postId).userId).name }}</b></p>
          <p>{{ postById(postId).text }}</p>
      </div>
  </div>
</template>

<script>
import sourceData from '@/data.json'
console.log(sourceData)

export default {
  data () {
    return {
      threads: sourceData.threads,
      posts: sourceData.posts,
      users: sourceData.users
    }
  },
  methods: {
    userById (userId) {
        return this.users.find(u => u.id === userId)
    },
    postById (postId) {
        return this.posts.find(p => p.id === postId)
    }
  }
}
</script>

<style>

</style>