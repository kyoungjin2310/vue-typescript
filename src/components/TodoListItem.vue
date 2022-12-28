<template>
  <li>
    <span>{{ item }}</span>
    <button @click="$emit('delete')">삭제</button>
  </li>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    item: String,
  },
});
</script>

<style scoped></style>
