<template>
  <div>
    <label for="todo-input">오늘 할일</label>
    <input id="todo-input" type="text" :value="item" @input="handleInput" />
    <button @click="addTodo">add</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    item: {
      type: String,
      required: true,
    },
  },
  methods: {
    handleInput(event: InputEvent) {
      if (event.target) {
        return;
      }
      this.$emit('inputEvent', event.target.value);
    },
    addTodo() {
      this.$emit('add');
    },
  },
});
</script>

<style scoped></style>
