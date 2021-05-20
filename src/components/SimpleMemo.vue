<template>
  <div class="simple-memo" v-bind:style="{ backgroundColor: bgColor }">
    <slot />
  </div>
</template>

<script>
export default {
  props: {
    bgColor: {
      // type: String,
      // default: "orange",
      // required: true,
      validator(value) {
        return ["orange", "blue", "red"].includes(value)
      },
    },
  },
  created: function () {
    console.log(this.bgColor)
  },
}
</script>

<style scoped>
.simple-memo {
  margin: 4px;
  padding: 0.5rem;
  border-radius: 4px;
  background-color: orange;
  color: white;
}
</style>
