<script setup lang="ts">
import { ref } from 'vue';
import DropdownList from '../molecules/DropdownList.vue';
import type { OptionData } from '../atoms/DropdownOption.vue';

//Mock Broadway shows
const shows = ref<OptionData[]>([
  { id: 'lionking', label: 'The Lion King' },
  { id: 'wicked', label: 'Wicked' },
  { id: 'hamilton', label: 'Hamilton' },
  { id: 'chicago', label: 'Chicago' },
  { id: 'aladdin', label: 'Aladdin' },
]);
const open = ref(false);
const selected = ref<OptionData | null>(null);

function toggle() {
  open.value = !open.value;
}
function onSelect(option: OptionData) {
  selected.value = option;
  open.value = false;
}
</script>

<style>
.dropdown-container {
  width: 200px;
  position: relative;
}

.dropdown-trigger {
  border: 1px solid #aaa;
  padding: 10px;
  background: #fafafa;
  cursor: pointer;
}

.info {
  margin-top: 1rem;
  font-size: 1rem;
}
</style>
