<template>
  <div>
    <input v-model="subtitleText" placeholder="Enter subtitle text" />
    <button @click="addSubtitle">Add Subtitle</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      subtitleText: '',
    };
  },
  methods: {
    addSubtitle() {
      const subtitle = {
        time: this.currentTime,
        text: this.subtitleText,
      };
      this.$emit('addSubtitle', subtitle);
      this.subtitleText = '';
    },
  },
  computed: {
    currentTime() {
      return this.$store.state.currentTime; 
    },
  },
};
</script>
<style>
.subtitle-editor {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

.subtitle-editor input {
  width: 70%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.subtitle-editor button {
  margin-left: 10px;
  padding: 8px 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

</style>
