<template>
  <div class="form-page">
    <h1>FORM</h1>
    <form action=""></form>
    <input type="text" v-focus />
  </div>
</template>

<script>
import _ from "lodash";

export default {
  directives: {
    focus: {
      //紐付いている要素がDOMに挿入されるとき
      inserted: el => {
        el.focus(); //要素にfocusを当てる
      }
    }
  }
};
</script>

<style scoped></style>
