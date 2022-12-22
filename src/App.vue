<template>
  <div>
    <TodoInput />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TodoInput from './components/TodoInput.vue';

export default defineComponent({
  setup() {
    return {};
  },
  components: { TodoInput },
});
</script>

<style scoped></style>
