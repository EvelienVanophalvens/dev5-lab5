<script setup>
import VideoPlayer from "./components/Video/VideoPlayer.vue";
import VideoDetails from "./components/Video/VideoDetails.vue";
import Chat from "./components/chat/Chat.vue";

import {ref} from 'vue';
let newDescription = ref("");

const updateVideo = (description) => {
  console.log(description);
  newDescription.value = description;
};



</script>

<template>
  <div class="tiktok">
    <div>
      <VideoPlayer @update:video-Description="updateVideo" />
    </div>
    <div>
      <VideoDetails :description="newDescription" />
      <Chat />
    </div>
  </div>
</template>

<style scoped>
  .tiktok{
    display: grid;
    grid-template-columns: 1fr 1fr;
  }
</style>
