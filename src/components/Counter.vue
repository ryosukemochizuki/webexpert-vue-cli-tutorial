<!-- ❗️ .vueファイルの中で、<template>タグは、1つの子しか持てません。❗️ -->
<template>
  <div class="counter">
    <div>🔥{{ count }}🔥</div>
    <button v-on:click="countUp">+1</button>
  </div>
</template>

<script>
export default {
  props: {
    initialValue: {
      type: Number,
    },
  },
  data: function () {
    return {
      count: this.initialValue,
    }
  },
  methods: {
    countUp: function () {
      this.count += 1
    },
  },
}
</script>

<!-- ❗️ <style scoped>を使うと、CSSのスコープをこの.vueファイルに限定できます! ❗️ -->
<style scoped>
.counter {
  display: flex;
  align-items: center;
  justify-content: center;

  background-color: lightgreen;
}
</style>
