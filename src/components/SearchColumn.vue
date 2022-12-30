<script setup >
import { ref } from 'vue'

import VideoData from '../assets/videos.json'

// Components
import SearchTextHyperLink from '../components/SearchTextHyperLink.vue'
import SearchWelcome from '../components/SearchWelcome.vue'

const videos =  VideoData.videos

const input = ref('')

</script>

<template lang="pug">
.column
  input.searchBar(
    type='input' 
    @input="event => input = event.target.value"
    placeholder='Search in videos...'
    )
  div(v-if='input.length > 1')
    p(v-for='video in videos' :key='video.url')
      p(v-for='timeStamp in video.timeStamps.filter((timeStamp) => timeStamp.text.toLowerCase().includes(input.toLowerCase()))' :key='video.url')
        <SearchTextHyperLink  :video=video :timeStamp=timeStamp />
  div(v-else='')
    SearchWelcome
</template>
  
<style scoped> 
.searchBar {
  width: 1200px;
  border: none;
  margin-top: 12px;
  margin-bottom: 12px;
  height: 30px;
  border-radius: 15px;
  padding-left: 20px;
}
</style> 
