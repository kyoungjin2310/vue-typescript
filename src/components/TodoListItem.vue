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
    index: Number,
  },
  methods: {
    removeItem() {
      this.$emit('delete', this.index);
    },
  },
});
</script>

<style scoped></style>
