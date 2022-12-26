<template>
  <li>{{ item }}</li>
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
