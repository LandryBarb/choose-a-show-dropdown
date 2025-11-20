<script setup lang="ts">
interface Props {
  id: string;
  selected: boolean;
}

defineProps<Props>();
</script>

<template>
  <div role="option" :id="id" :aria-selected="selected">
    <slot></slot>
  </div>
</template>
