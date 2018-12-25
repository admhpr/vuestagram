<template>
  <div class="vuestagram-post">
    <div class="header level">
      <div class="level-left details">
        <figure class="image is-32x32">
          <img :src="post.userImage">
        </figure>
        <span @click="like" class="username">{{post.username}}</span>
      </div>
    </div>
    <div @dblclick="like">
      <div
        class="image-container"
        :class="post.filter"
        :style="{ backgroundImage: 'url(' + post.postImage + ')' }"
      ></div>
    </div>

    <div class="content">
      <div class="heart">
        <i class="far fa-heart fa-lg" :class="{'fas': this.post.hasBeenLiked}" @click="like"></i>
      </div>
      <p class="likes">{{post.likes}} likes</p>
      <p class="caption">
        <span>{{post.username}}</span>
        {{post.caption}}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Post",
  props: {
    post: Object
  },
  methods: {
    like() {
      this.post.hasBeenLiked ? this.post.likes-- : this.post.likes++;
      this.post.hasBeenLiked = !this.post.hasBeenLiked;
    }
  }
};
</script>

<style lang="scss" src="../styles/post.scss">
// Styles from stylesheet
</style>
