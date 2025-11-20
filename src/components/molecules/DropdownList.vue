<template>
  <div class="dropdown-list">
    <DropdownOption
      v-for="o in options"
      :key="o.id"
      :option="o"
      @select="choose"
    />
  </div>
</template>

<script setup lang="ts">
import DropdownOption, { type OptionData } from '../atoms/DropdownOption.vue';

const props = defineProps<{
  options: OptionData[];
}>();

const emit = defineEmits<{
  (e: 'select', value: OptionData): void;
}>();

function choose(option: OptionData) {
  emit('select', option);
}
</script>
<style>
.dropdown-list {
  border: 1px solid #aaa;
  width: 200px;
  background: #fff;
}
</style>
