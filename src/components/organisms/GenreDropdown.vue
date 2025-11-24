<script setup lang="ts">
import { ref, computed } from 'vue';
import DropdownTrigger from '../molecules/DropdownTrigger.vue';
import ListBoxContainerAtom from '../atoms/ListBoxContainerAtom.vue';   
import ListboxOptions from '../molecules/ListboxOptions.vue';

interface Option{
    id: string;
    label: string;
}

const options: Option[] = [
    { id: 'genre-1', label: 'Rock' },
    { id: 'genre-2', label: 'Pop' },
    { id: 'genre-3', label: 'Jazz' },
    { id: 'genre-4', label: 'Classical' },
    { id: 'genre-5', label: 'Hip-Hop' },
];

const triggerRef = ref<HTMLElement | null>(null);

const isOpen = ref(false);
const selectedIndex = ref(0);
const activeIndex = ref(0);

const activeId = computed(() => options[activeIndex.value]?.id || '');

function toggleDropdown() {
    isOpen.value = !isOpen.value;
}

function closeDropdown() {
    isOpen.value = false;
    triggerRef.value?.focus();
}

function onKeydown(event: KeyboardEvent) {
    if (!isOpen.value) return;

    switch (event.key) {
        case 'ArrowDown':
            event.preventDefault();
            activeIndex.value = (activeIndex.value + 1) % options.length;
            break;
        case 'ArrowUp':
            event.preventDefault();
            activeIndex.value =
                (activeIndex.value - 1 + options.length) % options.length;
            break;
        case 'Enter':
        case ' ':
            event.preventDefault();
            selectedIndex.value = activeIndex.value;
            closeDropdown();
            break;
        case 'Escape':
            event.preventDefault();
            closeDropdown();
            break;
        case 'Tab':
           isOpen.value = false;
            break;
    }
}
const selected = computed(() => {
  return options[selectedIndex] ?? options[0];
});
</script>

<template>
    <div>
        <DropdownTrigger
        :expanded="isOpen"
        controls="genre-list"
        @toggle="toggleDropdown"
        ref="triggerRef"
        >
        {{ selected.label }}
    </DropdownTrigger>

    <ListBoxContainerAtom
        id="genre-list"
        :activeId="activeId"
        :isOpen="isOpen"
        @keydown="onKeydown">

        <ListboxOptions
        :options="options"
        :selectedIndex="selectedIndex"/>
        </ListBoxContainerAtom>


    </div>
</template>