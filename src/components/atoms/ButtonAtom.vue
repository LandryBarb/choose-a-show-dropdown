<template>
  <button v-bind="$attrs">
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
import { type ButtonHTMLAttributes } from 'vue';

defineProps<ButtonHTMLAttributes>();
</script>
