<template>
  <div>
    <h1>bit Coin Check</h1>

    <section v-if="errored">
      <p>適切なリクエストではありません。管理者に問い合わせてください</p>
    </section>

    <section v-else>
      <div v-if="loading">
        <p>ローディング中です。</p>
      </div>
      <div v-else>
        <div v-for="currency in info" :key="currency.description">
          {{ currency.description }}: <span v-html="currency.symbol"></span>
          <span>{{ currency.rate_float | currencyDecimal }}</span>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from "axios"
export default {
  data() {
    return {
      info: null,
      errored: false,
      loading: true,
    }
  },
  filters: {
    currencyDecimal(value) {
      return value.toFixed(2)
    },
  },
  mounted() {
    // setInterval(() => {
    axios
      .get("https://api.coindesk.com/v1/bpi/currentprice.json")
      .then((res) => (this.info = res.data.bpi))
      .catch((error) => {
        console.log(error)
        this.errored = true
      })
      .finally(() => {
        this.loading = false
      })
    // }, 60000)
    // async awaitを使ったやり方
  },
}
</script>

<style></style>
