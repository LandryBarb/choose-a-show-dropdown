<script setup lang="ts">
import ButtonAtom from '../atoms/ButtonAtom.vue';

interface Props {
  expanded: boolean;
  controls: string; //Id if listbox
}

const props = defineProps<Props>();
const emit = defineEmits<{  // differnt syntax
  (e: 'toggle'): void;
}>();


</script>

<template>
  <ButtonAtom
    type="button"
    aria-haspopup="listbox"
    :aria-expanded="props.expanded"
    :aria-controls="props.controls"
    @click="emit('toggle')"
  >
    <slot>Select an option</slot>
  </ButtonAtom>

  </template>