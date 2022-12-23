<template>
  <div>
    <label for="todo-input"></label>
    <input id="todo-input" type="text" :value="item" @input="handleInput" />
    <button @click="addTodo">add</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    item: String,
  },
  methods: {
    handleInput(e: any) {
      this.$emit('input', e.target.value);
    },
    addTodo() {
      console.log('add');
    },
  },
});
</script>

<style scoped></style>
