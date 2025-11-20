<template>
  <ul
    class="dropdown-list"
    id="show-list"
    role="listbox"
    tabindex="0"
    :aria-activedescendant="activeId"
    :style="{ display: isOpen ? 'block' : 'none' }"
  >
    <DropdownOption
      v-for="o in props.options"
      :key="o.id"
      :option="o"
      @select="choose"
    />
  </ul>
</template>

<script setup lang="ts">
import DropdownOption, { type OptionData } from '../atoms/DropdownOption.vue';
import { computed, ref } from 'vue';

const isOpen = ref(false);
const activeIndex = ref(0);
const selectedIndex = ref(0);

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
  color: black;
}
</style>
