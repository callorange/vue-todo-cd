<template>
  <div>
    <todo-header></todo-header>
    <todo-input @add-todo="addItem"></todo-input>
    <todo-list ref="todoList" :list="todoItems" @remove-todo="removeItem"></todo-list>
    <todo-footer @clear-todo="clearItems"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from "@/components/TodoHeader.vue";
import TodoInput from "@/components/TodoInput.vue";
import TodoList from "@/components/TodoList.vue";
import TodoFooter from "@/components/TodoFooter.vue";

export default {
  name: "aaappp",
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter,
  },
  data() {
    return {
      todoItems: [],
    };
  },
  created() {
    this.fetchItems();
  },
  methods: {
    fetchItems() {
      for (var i = 0; i < localStorage.length; i++) {
        var item = localStorage.key(i);
        this.todoItems.push(item);
      }
    },
    addItem(value) {
      let check = this.todoItems.indexOf(value);

      if (check == -1) {
        localStorage.setItem(value, value);
        this.todoItems.push(value);
      } else {
        this.$refs.todoList.hightlightItem(check);
      }
    },
    removeItem(item, index) {
      localStorage.removeItem(item);
      this.todoItems.splice(index, 1);
    },
    clearItems() {
      localStorage.clear();
      this.todoItems = [];
    },
  },
};
</script>

<style></style>
