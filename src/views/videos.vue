<template lang="pug">
h6 Videos
    p(v-for='video in videos' :key='video.url')
        | {{video.title}}
</template>
  
<script>
  import VideoData from '../assets/videos.json'
  
  export default {
    data() {
      return {
        videos: VideoData['videos'],
      };
    },
  };
  </script>