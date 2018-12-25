<template>
  <div class="app-body">This is the Phone Body
    <app-post v-for="post in posts" :post="post" :key="posts.indexOf(post)"></app-post>
  </div>
</template>

<script>
import Post from "./Post";

export default {
  name: "PhoneBody",
  props: {
    posts: Array,
    filters: Array
  },
  components: {
    "app-post": Post
  }
};
</script>

<style lang="scss" src="../styles/body.scss">
// Styles from stylesheet
</style>
