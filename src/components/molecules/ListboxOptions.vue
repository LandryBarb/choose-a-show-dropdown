<script setup lang="ts">
import OptionsAtom from '../atoms/OptionsAtom.vue';

interface Option{
    id: string;
    label: string;
}

interface Props {
    options: Option[];
    selectedIndex: number;
    // activeId: string;
    // isOpen: boolean;
}

defineProps<Props>();
</script>
<template>
    <template v-for="(opt, i) in options" :key="opt.id">
        <li>
          <OptionsAtom
          :id="opt.id"
        :selected="i === selectedIndex"
        >
        {{ opt.label }}
    </OptionsAtom>
        </li>
       

    </template>

</template>