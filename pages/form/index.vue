<template>
  <div class="form-page">
    <h1>FORM</h1>
    <form action=""></form>
    <select v-model="current" name="" id="">
      <option v-for="topic in topics" :value="topic.value" :key="topic.name">
        {{ topic.name }}
      </option>
    </select>
    <div>{{ current }}</div>
    <ul>
      <li v-for="item in list" :key="item.id">{{ item.id }}</li>
    </ul>
  </div>
</template>

<script>
import _ from "lodash";
import axios from "axios";

export default {
  data() {
    return {
      list: [],
      current: "",
      topics: [
        { value: "vue", name: "Vue.js" },
        { value: "jQuery", name: "jQuery" }
      ]
    };
  },
  computed: {},
  watch: {
    current: function(val) {
      // GitHubのAPIからトピックのリポジトリを検索
      axios
        .get("https://api.github.com/search/repositories", {
          params: {
            q: "topic:" + val
          }
        })
        .then(
          function(response) {
            this.list = response.data.items;
          }.bind(this)
        );
    }
  }
};
</script>

<style scoped></style>
