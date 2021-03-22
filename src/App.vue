<template>
  <div class="container">
    <SearchBar @termChange="onSearchTerm"></SearchBar>
    <div class="row">
      <VideoDetails :video="video"></VideoDetails>
      <VideoList :videos="videos" @playVideo="playVideo"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetails from "./components/VideoDetails";
const API_KAY = "AIzaSyBWl-QKQHeYVqWQZpyLn3AMuJFdCi3jzAU";

export default {
  name: "App",
  data() {
    return {
      videos: [],
      video: null,
    };
  },
  components: {
    SearchBar,
    VideoList,
    VideoDetails,
  },
  methods: {
    onSearchTerm(term) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KAY,
            q: term,
            type: "video",
            part: "snippet",
          },
        })
        .then((resposne) => (this.videos = resposne.data.items))
        .catch((err) => console.log(err));
    },
    playVideo(video) {
      this.video = video;
    },
  },
};
</script>

<style scoped>
    
</style>