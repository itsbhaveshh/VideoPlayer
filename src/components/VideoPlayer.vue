<template>
    <div>
      <input type="file" accept="video/*" @change="handleFileChange" />
      <video ref="video" :src="localVideoUrl" @timeupdate="updateCurrentTime" controls></video>
    </div>
  </template>
  
  <script>
  export default {
    props: ['videoUrl', 'subtitles'],
    data() {
      return {
        localVideoUrl: this.videoUrl, // Initialize local copy with prop value
      };
    },
    methods: {
      updateCurrentTime(event) {
        this.$emit('updateCurrentTime', event.target.currentTime);
      },
      handleFileChange(event) {
        const file = event.target.files[0];
        if (file) {
          this.localVideoUrl = URL.createObjectURL(file); // Update local copy
          this.$refs.video.load();
        }
      },
    },
    watch: {
      localVideoUrl(newValue, oldValue) {
        if (newValue !== oldValue) {
          this.$refs.video.load();
        }
      },
    },
  };
  </script>
  <style>
 .video-container {
   position: relative;
 }
 
 .video-container video {
   width: 100%;
   max-width: 800px;
 }
 
 </style>
 