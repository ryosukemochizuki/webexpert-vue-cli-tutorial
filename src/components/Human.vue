<template>
  <div class="human">
    <div class="atama">
      <div>😊</div>
    </div>
    <div class="karada">
      <div>💪{{ cloth }}💪</div>
    </div>
    <div class="ashi">
      <div>🦵🦵</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    clothes: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      cloth: this.clothes,
    }
  },
}
</script>

<style>
.human {
  width: 10rem;
  font-size: 3rem;
  text-align: center;
}
</style>
