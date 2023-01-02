<template>
  <li>
    <span
      class="list-item"
      :class="item.done && 'complete'"
      @click="toggleItem"
      >{{ item.title }}</span
    >
    <button @click="removeItem">삭제</button>
  </li>
</template>

<script lang="ts">
import { Todo } from '@/App.vue';
import { defineComponent, PropType } from 'vue';

export default defineComponent({
  props: {
    //vue에서 props type을 정의하는 방식 - PropType<generic>
    item: Object as PropType<Todo>,
    index: Number,
  },
  methods: {
    removeItem() {
      this.$emit('delete', this.index);
    },
    toggleItem() {
      this.$emit('toggle', this.item, this.index);
    },
  },
});
</script>

<style scoped>
.item {
  cursor: pointer;
}
.complete {
  text-decoration: line-through;
}
</style>
