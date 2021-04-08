<template>
  <div class="form-page">
    <h1>FORM</h1>
    <form action=""></form>

    <div>width: {{ width }}</div>
    <div>half width: {{ halfWidth }}</div>
    <input type="text" v-model.numver="halfWidth" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      width: 800,
      height: 500
    };
  },
  computed: {
    halfWidth: {
      get: function() {
        return this.width / 2;
      },
      set: function(val) {
        this.width = val * 2;
      }
    },
    halfHeight: function() {
      return this.height / 2;
    }
  }
};
</script>

<style scoped></style>
