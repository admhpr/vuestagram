<template>
  <div id="app">
    <div class="app">
      <div class="app-header">
        <img src="./assets/vuestagram.png">
      </div>
      <app-body :posts="posts" :filters="filters"/>
      <div class="app-footer">
        <div class="home-cta">
          <i class="fas fa-home fa-lg"></i>
        </div>
        <div class="upload-cta">
          <i class="far fa-plus-square fa-lg"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Body from "./components/Body";

import posts from "./data/posts";
import filters from "./data/filters";

export default {
  name: "App",
  data() {
    return {
      posts,
      filters
    };
  },
  components: {
    "app-body": Body
  }
};
</script>

<style lang="scss" src="./styles/app.scss">
// Styles from stylesheet
</style>
