<template>
  <div class="form-page">
    <h1>FORM</h1>
    <form action=""></form>
    <p>{{ width }} の半分は {{ halfWidth }}</p>
    <P>half height {{ halfPoint.y }}</P>
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
    halfWidth: function() {
      return this.width / 2;
    },
    halfHeight: function() {
      return this.height / 2;
    },
    // 「width × height」の中心座標をオブジェクトで返す
    halfPoint: function() {
      return {
        x: this.halfWidth,
        y: this.halfHeight
      };
    }
  }
};
</script>

<style scoped></style>
