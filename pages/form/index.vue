<template>
  <div class="form-page">
    <h1>FORM</h1>
    <form action=""></form>
    <button @click="video1 = true"></button>
    <button @click="video1 = false"></button>
    <video v-video="video1"></video>

    <button @click="video2 = true"></button>
    <button @click="video2 = false"></button>
    <video v-video="video2"></video>
  </div>
</template>

<script>
import _ from "lodash";

export default {
  data() {
    return {
      video1: false,
      video2: false
    };
  },
  directives: {
    video(el, binding) {
      binding.value ? el.play() : el.pause();
    }
  }
};
</script>

<style scoped></style>
