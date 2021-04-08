<template>
  <div class="form-page">
    <h1>FORM</h1>
    <form action=""></form>

    <div>width: {{ width }}</div>
    <div>half width: {{ halfWidth }}</div>
    <input type="text" v-model.numver="halfWidth" />

    <p>算出プロパティ</p>
    <ol>
      <li>Original : <input type="text" v-model="computedNumber" /></li>
      <li>Even/ Odd : {{ computedResult }}</li>
    </ol>
    <p>メソッド</p>
    <ol>
      <li>Original : <input type="text" v-model="methodNumber" /></li>
      <li>Even/ Odd : {{ methodResult() }}</li>
    </ol>
  </div>
</template>

<script>
export default {
  data() {
    return {
      width: 800,
      height: 500,
      computedNumber: 4,
      methodNumber: 4
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
    },
    computedResult: {
      get() {
        return this.computedNumber % 2 === 0 ? "Even" : "Odd";
      },
      set() {
        return (this.computedNumber = this.computedNumber);
      }
    }
  },
  methods: {
    methodResult: function() {
      return this.methodNumber % 2 === 0 ? "Even" : "Odd";
    }
  }
};
</script>

<style scoped></style>
