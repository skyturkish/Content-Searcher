<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
import Video from "./components/videos.vue";
</script>

<template lang="pug">
.wrapper  
    Video
</template>

<style>
.wrapper {
  justify-content: center;
}
</style>
