<template>
  <div class="form-page">
    <h1>FORM</h1>
    <form action=""></form>
    <ul>
      <li v-for="item in list" :key="item.id">
        {{ item.name }} {{ item.price }}円
      </li>
    </ul>
    <input v-model.number="budget" /> 円以下に絞り込む
    <input v-model.number="limit" /> 件を表示
    <button :click="(sortedByAsc = !sortedByAsc)">
      {{ sortedByAsc ? "降順↓へ切り替え" : "昇順↑に切り替え" }}
    </button>
    <p>
      {{ matchedBudgetItems.length }} 件中、 {{ limitedItems.length }} 件を表示
    </p>
    <ul>
      <li v-for="item in filteredList" :key="item.id">
        {{ item.name }} {{ item.price }} 円
      </li>
    </ul>
  </div>
</template>

<script>
import _ from "lodash";

export default {
  data() {
    return {
      sortedByAsc: false,
      budget: 300,
      limit: 2,
      list: [
        { id: 1, name: "りんご", price: 100 },
        { id: 2, name: "バナナ", price: 145 },
        { id: 3, name: "いちご", price: 380 },
        { id: 4, name: "オレンジ", price: 200 },
        { id: 5, name: "メロン", price: 900 }
      ]
    };
  },
  computed: {
    matchedBudgetItems: function() {
      return this.list.filter(item => {
        item.price <= this.budget;
      }, this);
    },
    sortedItems: function() {
      return _.orderBy(
        this.matchedBudgetItems,
        "price",
        this.sortedByAsc ? "asc" : "desc"
      );
    },
    limitedItems: function() {
      return this.sortedItems.slice(0, this.limit);
    },

    filteredList: function() {
      return this.limitedItems;
    }
  },
  methods: {}
};
</script>

<style scoped></style>
