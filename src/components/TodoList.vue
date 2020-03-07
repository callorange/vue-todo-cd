<template>
  <div>
    <ul>
      <li v-for="(item, index) in list" :key="index" ref="todoItemElements">
        <span>{{ item }}</span>
        <button @click="removeItem(item, index)">remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
// import { bus } from "../utils/bus";

export default {
  props: {
    list: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    removeItem(item, index) {
      this.$emit("remove-todo", item, index);
    },
    hightlightItem(index) {
      this.$refs.todoItemElements.forEach(element => {
        element.classList.remove("highlight");
      });
      let el = this.$refs.todoItemElements[index];
      el.classList.add("highlight");
    },
  },
  // beforeMount() {
  //   bus.$on("remove-all", this.clearItems);
  // },
  // beforeDestroy() {
  //   bus.$off("remove-all", this.clearItems);
  // }
};
</script>

<style scoped>
.highlight {
  background-image: linear-gradient(
    -100deg,
    rgba(255, 255, 255, 0),
    yellow 85%,
    rgba(255, 255, 255, 0)
  );
}
</style>
