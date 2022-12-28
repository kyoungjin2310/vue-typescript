<template>
  <li>
    <span>{{ item }}</span>
    <button @click="removeItem">삭제</button>
  </li>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    item: String,
  },
  methods: {
    removeItem() {
      this.$emit('delete');
    },
  },
});
</script>

<style scoped></style>
