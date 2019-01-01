<template>
  <div id="main">
    <div class="app-phone">
      <div class="phone-header">
        <img src="./assets/vuestagram.png">
        <a class="cancel-cta" v-if="step === 2 || step === 3" @click="goToHome">Cancel</a>
        <a class="next-cta" v-if="step === 2" @click="step++">Next</a>
        <a class="next-cta" v-if="step === 3" @click="sharePost">Share</a>
      </div>
      <phone-body
        :step="step"
        :posts="posts"
        :filters="filters"
        :image="image"
        :selectedFilter="selectedFilter"
        v-model="caption"
      />
      <div class="phone-footer">
        <div class="home-cta" @click="goToHome">
          <i class="fas fa-home fa-lg"></i>
        </div>
        <div class="upload-cta">
          <input
            type="file"
            name="file"
            id="file"
            class="inputfile"
            @change="uploadImage"
            :disabled="step !== 1"
          >
          <label for="file">
            <i class="far fa-plus-square fa-lg"></i>
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import EventBus from "./utils/event-bus.js";
import PhoneBody from "./components/PhoneBody";

// mock data
import posts from "./data/posts";
import filters from "./data/filters";

export default {
  name: "App",
  data() {
    return {
      step: 1,
      posts,
      filters,
      image: "",
      selectedFilter: "",
      caption: ""
    };
  },
  created() {
    EventBus.$on("filter-selected", evt => {
      this.selectedFilter = evt.filter;
    });
  },
  methods: {
    goToHome() {
      this.image = "";
      this.selectedFilter = "";
      this.caption = "";
      this.step = 1;
    },
    uploadImage(evt) {
      const files = evt.target.files;
      if (!files.length) return;

      const reader = new FileReader();
      reader.readAsDataURL(files[0]);
      reader.onload = evt => {
        this.image = evt.target.result;
        this.step = 2;
      };

      // To enable reuploading of same files in Chrome
      document.querySelector("#file").value = "";
    },
    sharePost() {
      const post = {
        username: "webmaster95",
        userImage: "https://api.adorable.io/avatars/285/abott@adorable.png",
        postImage: this.image,
        likes: 0,
        caption: this.caption,
        filter: this.filterType
      };
      this.posts.unshift(post);
      this.goToHome();
    }
  },
  components: {
    "phone-body": PhoneBody
  }
};
</script>

<style lang="scss" src="./styles/app.scss">
// Styles from stylesheet
</style>
