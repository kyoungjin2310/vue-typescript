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
      <!-- <TodoInput
        v-model="test"
        :item="test"
        @inputEvent="updateVmodel"
        @add="addTodoItem"
      /> -->
      <div>
        <ul>
          <TodoListItem
            v-for="(item, index) in todoItems"
            :key="index"
            :index="index"
            :item="item"
            @toggle="toggleTodoItemComplete"
            @delete="removeTodoItem"
          />
        </ul>
      </div>
    </main>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TodoInput from './components/TodoInput.vue';
import TodoListItem from './components/TodoListItem.vue';

export interface Todo {
  title: string;
  done: boolean;
}

const STORAGE_KEY = 'vue-todo-ts-vi';
const storage = {
  save(todos: Todo[]) {
    const parse = JSON.stringify(todos);
    localStorage.setItem(STORAGE_KEY, parse);
  },
  fetch(): Todo[] {
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
      todoItems: [] as Todo[],
    };
  },
  created() {
    this.fetchTodoItems();
  },
  methods: {
    //ordering(정렬) - sort이용
    // 클경우 : 1, 작을경우 : -1
    fatchTodoItems() {
      this.todoItems = storage.fetch().sort((a, b) => {
        if (a.title < b.title) {
          return -1;
        }
        if (a.title > b.title) {
          return 1;
        }
        return 0;
      });
    },
    updateTodoText(val: string) {
      this.todoTxt = val;
    },
    addTodoItem(val) {
      // localStorage.setItem(val, val);
      this.todoText = val;
      const todo: Todo = {
        title: this.todoText,
        done: false,
      };
      this.todoItems.push(todo);
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
    removeTodoItem(index: number) {
      this.todoItems.splice(index, 1);
      storage.save(this.todoItems);
    },
    toggleTodoItemComplete(todoItem: Todo, index: number) {
      this.todoItems.splice(index, 1, {
        ...todoItem,
        done: !todoItem.done,
      });
      storage.save(this.todoItems);
    },
  },
});
</script>

<style scoped></style>
