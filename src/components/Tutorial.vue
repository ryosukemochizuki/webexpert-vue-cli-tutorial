<template>
  <!-- ❗️ .vueファイルの中で、<template>タグは、1つの子しか持てません。❗️ -->
  <div class="tutorial">
    <div>
      <h1>
        <TutorialIcon></TutorialIcon>
        <slot></slot>
        <TutorialIcon></TutorialIcon>
      </h1>
      <p>
        Vue CLIでの開発は、new
        Vueを使った開発と異なる部分が数点ありますが、より便利に開発できます。<br />
        このTutorialコンポーネントを参考にして、いくつかのアプリを.vueファイルで開発してみましょう!
      </p>
    </div>
  </div>
</template>

<script>
import TutorialIcon from "./TutorialIcon.vue"
export default {
  components: {
    TutorialIcon,
  },
  data() {},
}
</script>

<!-- ❗️ <style scoped>を使うと、CSSのスコープをこの.vueファイルに限定できます! ❗️ -->
<style scoped>
.tutorial {
  text-align: center;
}
</style>
