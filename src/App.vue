<template>
  <div>
    <TodoInput :item="todoTxt" @input="updateTodoText" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TodoInput from './components/TodoInput.vue';

export default defineComponent({
  components: { TodoInput },
  data() {
    return {
      todoTxt: '',
    };
  },
  methods: {
    updateTodoText(val: string) {
      this.todoTxt = val;
    },
  },
});
</script>

<style scoped></style>
