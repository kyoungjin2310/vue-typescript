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
      const eventTarget = event.target as HTMLInputElement;
      this.$emit('inputEvent', eventTarget.value);
    },
    addTodo() {
      this.$emit('add', this.item);
    },
  },
});
</script>

<style scoped></style>
