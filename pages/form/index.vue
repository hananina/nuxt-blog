<template>
  <div class="form-page">
    <h1>FORM</h1>
    <form action=""></form>
    <p>{{ width }} の半分は {{ halfWidth }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      width: 800
    };
  },
  computed: {
    // 算出プロパティhalfWidthを定義
    halfWidth: function() {
      return this.width / 2;
    }
  }
};
</script>

<style scoped></style>
