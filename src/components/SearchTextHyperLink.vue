<script setup >
const props = defineProps({
  video : {
    type: Map,
    required: true
  },
  timeStamp: {
    type: Map,
    required: true
  }
})

function startWith(timeStamp) {
  const time = timeStamp.time.split(':')

  const minute = time[0]

  const second = time[1]
  
  const startSecond = parseInt(minute) * 60 + parseInt(second)
  
  return '&t=' + startSecond + 's'
}

</script>

<template lang="pug">
.link
  a(:href='video.url + startWith(timeStamp)' target='_blank') {{ timeStamp.text }} {{ video.createdAt }} 
</template>

<style scoped> 
.link{
  margin-bottom:10px;
}
</style> 
