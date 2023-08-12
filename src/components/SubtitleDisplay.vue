<template>
    <div>
      <div v-for="subtitle in subtitles" :key="subtitle.time">
        <p v-if="currentTime >= subtitle.time">{{ subtitle.text }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['subtitles', 'currentTime'],
  };
  </script>
  <style>
  .subtitle-container {
    margin-top: 20px;
  }
  
  .subtitle {
    display: none;
    background-color: rgba(0, 0, 0, 0.7);
    color: #fff;
    padding: 5px 10px;
    border-radius: 4px;
    position: absolute;
    bottom: 10px;
    left: 50%;
    transform: translateX(-50%);
  }
  
  .subtitle.show {
    display: block;
  }
  
  </style>
  