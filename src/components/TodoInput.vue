<template>
  <div>
    <input type="text" v-model="inputText" @keyup.enter="addItem" />
    <button @click="addItem">add</button>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      inputText: "",
    };
  },
  methods: {
    addItem() {
      this.$emit("add-todo", this.inputText);
      this.inputText = "";
    },
  },
};
</script>

<style></style>
