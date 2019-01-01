<template>
  <div class="filter-type">
    <p>{{filter.name}}</p>
    <!-- styling coming from cssgram -->
    <div
      class="img"
      :class="filter.name"
      :style="{ backgroundImage: 'url(' + image + ')' }"
      @click="selectedFilter"
    ></div>
  </div>
</template>

<script>
import EventBus from "../utils/event-bus.js";
export default {
  name: "FilterType",
  props: {
    filter: Object,
    image: String
  },
  methods: {
    selectedFilter() {
      EventBus.$emit("filter-selected", { filter: this.filter.name });
    }
  }
};
</script>

<style lang="scss" src="../styles/filter-type.scss">
// Styles from stylesheet
</style>
