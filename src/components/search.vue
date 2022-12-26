<script setup >
import { ref } from 'vue'

import VideoData from '../assets/videos.json'

const videos =  VideoData['videos']

const input = ref('');

const isValid = ref( input.value.length > 2 )

function startWith(timeStamp) {
  const time = timeStamp.time.split(':')

  const minute = time[0]

  const second = time[1]
  
  const startSecond = parseInt(minute) * 60 + parseInt(second)
  
  return '&t=' + startSecond + 's'
}


</script>

<template lang="pug">
.body
  input.searchBar(
    type='input' 
    v-model='input' 
    placeholder='Search in videos...'
    )
  <div v-if="input.length > 1">
  p.timeStamps(v-for='video in videos' :key='video.url')
    p(v-for='timeStamp in video.timeStamps.filter((timeStamp) => timeStamp.text.toLowerCase().includes(input.toLowerCase()))' :key='video.url')
      .link
      a(:href='video.url + startWith(timeStamp)' target='_blank') {{timeStamp.text}}
  </div>
  <div v-else>
  Now find what are you looking for 
  </div>
</template>
  
<style scoped> 
.body{
  margin: 0px;
  height: 1000px;
}
.searchBar {
  width: 1200px;
  border: none;
  margin-top: 12px;
  margin-bottom: 12px;
  height: 30px;
  border-radius: 15px;
  padding-left: 20px;

}
.timeStamps {
  width: max-content;
}
.link{
  width:max-content;
  margin-bottom:10px;
}

</style> 
