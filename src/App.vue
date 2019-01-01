<template>
  <div id="app">
    <div class="app-phone">
      <div class="phone-header">
        <img src="./assets/vuestagram.png">
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
        <div class="home-cta">
          <i class="fas fa-home fa-lg"></i>
        </div>
        <div class="upload-cta">
          <input type="file" name="file" id="file" class="inputfile" @change="uploadImage">
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
