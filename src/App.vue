<template>
  <div id="app">
    <Tutorial :style="{ marginTop: 3.75 + 'rem' }"
      >WebExpertコース Vue CLI チュートリアル</Tutorial
    >
    <Tutorial :style="{ margintop: 3.75 + 'rem' }"
      >iPhoneコース Swiftチュートリアル</Tutorial
    >
    <Tutorial :style="{ margintop: 3.75 + 'rem' }"
      >Webコース Ruby on Railsチュートリアル</Tutorial
    >
    <Counter :initialValue="10"></Counter>

    <Todo />

    <simple-memo bgColor="orange"> メモ１ </simple-memo>

    <simple-memo bgColor="blue"> メモ２ </simple-memo>

    <div class="container">
      <Human clothes="🎽" />
      <Human clothes="👔" />
      <Human clothes="👕" />
    </div>

    <coin-desk />
  </div>
</template>

<script>
import Tutorial from "@/components/Tutorial.vue"
import Counter from "@/components/Counter.vue"
import Todo from "@/components/Todo.vue"
import SimpleMemo from "@/components/SimpleMemo.vue"
import Human from "@/components/Human"
import coinDesk from "@/components/CoinDesk"
import CoinDesk from "./components/CoinDesk.vue"
export default {
  name: "App",
  components: {
    Tutorial,
    Counter,
    Todo,
    SimpleMemo,
    Human,
    coinDesk,
    CoinDesk,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.container {
  display: flex;
}
</style>
