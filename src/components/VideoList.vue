<template>
  <div class="list-group col-md-4">
      <VideoItem
        @videoSelect="onVideoSelect"
        v-for="video in videos" 
        :video="video" 
        :key="video.etag">
      </VideoItem>
  </div>
</template>

<script>
import VideoItem from './VideoItem';

export default {
    name: 'VideoList',
    props: {
        "videos": Array
    },
    components: {
        VideoItem
    },
    methods: {
        onVideoSelect(video) {
            this.$emit("playVideo", video)
        }
    }
}
</script>

<style>

</style>