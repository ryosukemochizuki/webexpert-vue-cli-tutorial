<template>
  <div id="editor">
    <!-- マークダウンを打つ -->
    <textarea :value="input" @input="update"></textarea>
    <!-- リアルタイムで表示する -->
    <div v-html="compiledMarkdown"></div>
  </div>
</template>

<script>
// ライブラリのimport
const _ = require("lodash") // 遅延
const marked = require("marked") // HTML要素の中のマークダウン記法を判断して変換する

export default {
  data: function () {
    return {
      input: "# hello",
    }
  },
  computed: {
    compiledMarkdown: function () {
      return marked(this.input, { sanitize: true })
    },
  },
  methods: {
    update: _.debounce(function (e) {
      this.input = e.target.value
    }, 300),
  },
}
// v-modelで更新すればmethodsはいらないが、今回はdebounceを使いたいためわざと分けた
</script>

<style></style>
