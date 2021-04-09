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
    <button @click="update">更新</button>
    <button @click="sortedByAsc = !sortedByAsc">切り替え</button>
    <p>
      {{ matchedBudgetItems.length }} 件中、 {{ limitedItems.length }} 件を表示
    </p>
    <ul>
      <li v-for="item in limitedItems" :key="item.id">
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
        return item.price < this.budget;
      }, this);
    },
    sortedItems() {
      return _.orderBy(
        this.matchedBudgetItems,
        "price",
        this.sortedByAsc ? "desc" : "asc"
      );
    },
    limitedItems: function() {
      return this.sortedItems.slice(0, this.limit);
    }
  },
  methods: {
    update() {
      this.list[0].name = "Updatedりんご";
    }
  },
  watch: {
    list: {
      handler: function(newVal, oldVal) {
        // listが変化したときに行いたい処理
        console.log("piiiiii updated");
      },
      deep: true, //ネストされたオブジェクトも監視する
      immediate: true //初期読み込みでも呼び出す
    }
  },
  created() {
    this.$watch(
      () => {
        //処理
        return [this.budget, this.limit];
      },
      () => {
        //budget limitが変化したよ
        console.log("created のwatch | budget limitが変化したよ");
      }
    );
  }
};
</script>

<style scoped></style>
