<template>
  <div class="phone-body">
    <div class="feed">
      <post v-for="post in posts" :post="post" :key="posts.indexOf(post)"></post>
    </div>
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
    post: Post
  }
};
</script>

<style lang="scss" src="../styles/phone-body.scss">
// Styles from stylesheet
</style>
