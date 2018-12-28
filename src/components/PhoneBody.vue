<template>
  <div class="phone-body">
    <div v-if="step === 1" class="feed">
      <post v-for="post in posts" :post="post" :key="posts.indexOf(post)"></post>
    </div>
    <div v-if="step === 2">
      <div class="selected-image" :style="{ backgroundImage: 'url(' + image + ')' }"></div>
      <div class="filter-container">Step two
        <!-- Where filter choices will be -->
      </div>
    </div>
  </div>
</template>


<script>
import Post from "./Post";
export default {
  name: "PhoneBody",
  props: {
    step: Number,
    posts: Array,
    filters: Array,
    image: String
  },
  components: {
    post: Post
  }
};
</script>

<style lang="scss" src="../styles/phone-body.scss">
// Styles from stylesheet
</style>
