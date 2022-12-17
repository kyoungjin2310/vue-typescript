<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <TodoInput msg="Welcome to Your Vue.js + TypeScript App" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TodoInput from '@/components/TodoInput.vue'; // @ is an alias to /src

export default defineComponent({
  name: 'TodoInput',
  components: {
    TodoInput,
  },
});
</script>
