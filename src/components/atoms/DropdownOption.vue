<template>
  <div class="dropdown-option" @click="select">
    {{ option.label }}
  </div>
</template>

<script setup lang="ts">
export interface OptionData {
  id: string;
  label: string;
}
const props = defineProps<{
  option: OptionData;
}>();

const emit = defineEmits<{
  (e: 'select', value: OptionData): void;
}>();

function select() {
  emit('select', props.option);
}
</script>

<style>
.dropdown-option {
  padding: 8px 12px;
  border-bottom: 1px solid #ddd;
  cursor: pointer;
}

.dropdown-option:hover {
  background: #eee;
}
</style>
