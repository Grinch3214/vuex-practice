<template>
  <div id="app">
    <post-form />
    <hr>
    <h1>{{ postsCount }}</h1>
    <div class="posts" v-for="post in validPosts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
import PostForm from './components/PostForm.vue'

export default {
  name: 'App',
  components: {
    PostForm
  },
  computed: mapGetters(['validPosts', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  async mounted() {
    this.fetchPosts(5);
  }
}
</script>

<style>
#app {
  margin: 60px auto;
  max-width: 400px;
  text-align: center;
}
.posts {
  border: 1px solid #ccc;
  padding: 8px;
  margin-bottom: 15px;
  border-radius: 4px;
}
</style>
