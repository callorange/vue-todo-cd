<template>
  <div>
    <h1>footer</h1>
    <button @click="clear">clear all</button>
  </div>
</template>

<script>
// import { bus } from "../utils/bus";

export default {
  methods: {
    clear() {
      this.$emit("clear-todo");
      // bus.$emit("remove-all");
    },
  },
};
</script>

<style></style>
