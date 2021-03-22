<template>
  <div v-if="video" class="col-md-8">
    <div class="ratio ratio-16x9">
      <iframe :src="videoUrl" frameborder="0"></iframe>
    </div>
    <div class="details">
      <h4>
        {{ video.snippet.title }}
      </h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetails",
  props: {
    video: Object,
  },
  computed: {
    videoUrl() {
      const { videoId } = this.video.id;
      return `https://www.youtube.com/embed/${videoId}`;
    },
  },
};
</script>

<style>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid black;
  border-radius: 4px;
}
</style>