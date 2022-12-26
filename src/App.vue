<template>
  <div>
    <header>
      <h1>Ts</h1>
    </header>
    <main>
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
      <div>
        <ul>
          <TodoListItem />
          <li>아이템 1</li>
          <li>아이템 2</li>
          <li>아이템 3</li>
        </ul>
      </div>
    </main>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TodoInput from './components/TodoInput.vue';
import TodoListItem from './components/TodoListItem.vue';

const STORAGE_KEY = 'vue-todo-ts-vi';
const storage = {
  save(todos: string[]) {
    const parse = JSON.stringify(todos);
    localStorage.setItem(STORAGE_KEY, parse);
  },
  fetch() {
    //localStorage는 json이라 빈배열을 string으로 바꿔줌
    const todoItems = localStorage.getItem(STORAGE_KEY) || '[]';
    const result = JSON.parse(todoItems);
    return result;
  },
};

export default defineComponent({
  components: { TodoInput, TodoListItem },
  data() {
    return {
      todoTxt: '',
      test: '',
      todoItems: [],
    };
  },
  methods: {
    updateTodoText(val: string[]) {
      this.todoTxt = val;
    },
    addTodoItem() {
      const val = this.todoText;
      // localStorage.setItem(val, val);
      this.todoItems.push(val);
      storage.save(this.todoItems);
      this.initTodoText();
    },
    initTodoText() {
      this.todoText = '';
    },
    updateVmodel(val: string) {
      this.test = val;
    },
    fetchTodoItems() {
      this.todoItems = storage.fetch();
    },
  },
  created() {
    this.fetchTodoItems();
  },
});
</script>

<style scoped></style>
