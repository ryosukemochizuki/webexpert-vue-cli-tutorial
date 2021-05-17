<template>
  <div id="app">
    <Tutorial :style="{ marginTop: 3.75 + 'rem' }"
      >WebExpertコース Vue CLI チュートリアル</Tutorial
    >
    <Tutorial :style="{ marginTop: 3.75 + 'rem' }"
      >iPhoneコース Swiftチュートリアル</Tutorial
    >
    <Tutorial :style="{ marginTop: 3.75 + 'rem' }"
      >Webコース Ruby on Railsチュートリアル</Tutorial
    >
    <Counter :initialValue="10"></Counter>

    <Todo />
  </div>
</template>

<script>
import Tutorial from "@/components/Tutorial.vue"
import Counter from "@/components/Counter.vue"
import Todo from "@/components/Todo.vue"
export default {
  name: "App",
  components: {
    Tutorial,
    Counter,
    Todo,
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
</style>
