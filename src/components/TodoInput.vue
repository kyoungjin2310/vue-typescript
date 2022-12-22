<template>
  <div>
    <label for="todo-input"></label>
    <input id="todo-input" type="text" />
    <button @click="addTodo">add</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  setup() {
    return {};
  },
  methods: {
    addTodo() {
      console.log('add');
    },
  },
});
</script>

<style scoped></style>
