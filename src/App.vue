<template>
  <div>
    <!-- 부모컴포넌트에서 값을 자식컴포넌트로 
    내려주고 data를 부모 컴포넌트에서 관리하는 방식 -->
    <TodoInput :item="todoTxt" @input="updateTodoText" @add="addTodoItem" />
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
    addTodoItem() {
      const val = this.todoText;
      localStorage.setItem(val, val);
      this.initTodoText();
    },
    initTodoText() {
      this.todoText = '';
    },
  },
});
</script>

<style scoped></style>
