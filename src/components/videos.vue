<script setup >
import {ref } from 'vue'

import VideoData from '../assets/videos.json'

const videos =  VideoData['videos']

const input = ref('');

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
  input.searchBar(type='input' v-model='input' placeholder='Search in videos...')
  h1 {{input}}
  h1.timeStamps Videos
  p(v-for='video in videos' :key='video.url')
    p(v-for='timeStamp in video.timeStamps.filter((timeStamp) => timeStamp.text.toLowerCase().includes(input.toLowerCase()))' :key='video.url')
      <a :href="video.url + startWith(timeStamp)">
        <button v-on:href="">{{timeStamp.text}} </button>
      </a>
  
</template>
  
<style scoped> 
.body 
{
    margin: 0;
    justify-content: flex-start;
    font-family: cursive;

  } 

.timeStamps {
  width:max-content;
  text-align: center;
  padding: 0px;
  text-align: center;
}

.title {
  background-color: #bd6969;
  font-size: 45px;
}
</style>
