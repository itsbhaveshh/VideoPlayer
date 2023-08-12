<template>
  <div id="app">
    <video-player ref="videoPlayer" :videoUrl="videoUrl" :subtitles="subtitles" />
    <subtitle-editor @addSubtitle="addSubtitle" />
    <subtitle-display :subtitles="subtitles" :currentTime="currentTime" />
  </div>
</template>

<script>
import VideoPlayer from './components/VideoPlayer.vue';
import SubtitleEditor from './components/SubtitleEditor.vue';
import SubtitleDisplay from './components/SubtitleDisplay.vue';

export default {
  name: 'App',
  components: {
    VideoPlayer,
    SubtitleEditor,
    SubtitleDisplay,
  },
  data() {
    return {
      videoUrl: '',
      subtitles: [],
      currentTime: 0,
    };
  },
  methods: {
    addSubtitle(subtitle) {
      this.subtitles.push(subtitle);
    },
  },
};
</script>


<style>
#app {
  text-align: center;
  padding: 20px;
}
</style>

