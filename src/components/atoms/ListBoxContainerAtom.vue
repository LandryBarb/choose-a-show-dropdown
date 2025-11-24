<script setup lang="ts">
interface Props {
  activeId: string;
  isOpen: boolean;
}

defineProps<Props>();
</script>

<template>
  <ul
    role="listbox"
    tabindex="0"
    :aria-activedescendant="activeId"
    :style="{ display: isOpen ? 'block' : 'none' }"
    v-bind="$attrs"
  >
    <slot></slot>
  </ul>
</template>
