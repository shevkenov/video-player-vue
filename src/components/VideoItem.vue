<template>
  <li class="list-group-item media" @click="videoSelect">
    <img :src="imageUrl" :alt="video.snippet.title" />
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoItem",
  props: {
    video: Object,
  },
  computed: {
    imageUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
      videoSelect() {
          this.$emit('videoSelect', this.video)
      }
  }
};
</script>

<style scoped>
    li {
        display: flex;
        cursor: pointer;
    }

    li:hover {
        background-color: #eee;
    }
</style>