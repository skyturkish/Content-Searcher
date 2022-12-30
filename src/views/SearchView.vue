<script setup>
import SearchColumn from "../components/SearchColumn.vue";
import GithubClickableIcon from "../components/clickableIcons/Github.vue"
import YoutubeClickableIcon from "../components/clickableIcons/Youtube.vue"

</script>

<template lang="pug">
.body
  GithubClickableIcon
  SearchColumn
  YoutubeClickableIcon
</template>

<style scoped>
.body {
  margin: 0px;
  height: 1000px;
  display: grid;
  gap: 1rem;
  grid-auto-flow: column;
  
}
</style>
