<template>
  <li class="dropdown-option" role="option" :id="option.id" @click="select">
    <div
      :id="option.id"
      :aria-selected="option.number === selectedIndex"
      :class="{ active: option.number === activeIndex }"
    ></div>
    {{ option.label }}
  </li>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const selectedIndex = ref(0);
const activeIndex = ref(0);

export interface OptionData {
  number: number;
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
  color: #000;
}

.dropdown-option:hover {
  background: #eee;
}
</style>
