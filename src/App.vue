<template>
  <div>
    <!-- 부모컴포넌트에서 값을 자식컴포넌트로 
    내려주고 data를 부모 컴포넌트에서 관리하는 방식 -->
    <TodoInput
      :item="todoTxt"
      @inputEvent="updateTodoText"
      @add="addTodoItem"
    />
    <!-- v-model로 사용할경우 @input: value 로 사용해야함 -->
    <TodoInput
      v-model="test"
      :item="test"
      @inputEvent="updateVmodel"
      @add="addTodoItem"
    />
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
      test: '',
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
    updateVmodel(val: string) {
      this.test = val;
    },
  },
});
</script>

<style scoped></style>
