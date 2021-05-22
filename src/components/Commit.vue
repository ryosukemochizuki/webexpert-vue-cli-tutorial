<template>
  <section>
    <h1>Latest Vue.js Commits</h1>
    <template v-for="branch in branches">
      <input
        type="radio"
        :id="branch"
        :value="branch"
        name="branch"
        :key="branch.id"
        v-model="currentBranch"
      />
      <label :for="branch" :key="branch.id">{{ branch }}</label>
    </template>
    <p>vuejs/vue@{{ currentBranch }}</p>
    <ul>
      <li v-for="record in commits" :key="record.id">
        <a :href="record.html_url" target="_blank" class="commit">{{
          record.sha.slice(0, 7)
        }}</a>
        - <span class="message">{{ record.commit.message | truncate }}</span
        ><br />
        by
        <span class="author"
          ><a :href="record.author.html_url" target="_blank">{{
            record.commit.author.name
          }}</a></span
        >
        at
        <span class="date">{{ record.commit.author.date | formatDate }}</span>
      </li>
    </ul>
  </section>
</template>

<script>
const apiURL =
  "https://api.github.com/repos/ryosukemochizuki/js-recipe/commits?per_page=5&sha="
export default {
  data: function () {
    return {
      branches: ["master", "dev"], // 今回はブランチ分けてないからdevなし(切り替えはできる)
      currentBranch: "master",
      commits: null,
    }
  },

  created: function () {
    // 読み込んだらdefaultの値でデータをとってくる
    this.fetchData()
  },

  watch: {
    // currentBranchが変更されたらfetchdataを実行できる？
    currentBranch: "fetchData",
  },

  // filters→引数 | filtersメソッド で実現
  filters: {
    // コミットメッセージに空白があったらそこで切る
    truncate: function (v) {
      var newline = v.indexOf("\n")
      return newline > 0 ? v.slice(0, newline) : v
    },
    // 日付のいらないとこ消去
    formatDate: function (v) {
      return v.replace(/T|Z/g, " ")
    },
  },

  methods: {
    // データ取る非同期処理
    fetchData: async function () {
      // fetchを使ったバージョン
      const res = await fetch(apiURL + this.currentBranch)
      const data = await res.json()
      this.commits = data
      // console.log(this.commits[0].html_url)
    },
  },
}
</script>

<style></style>
