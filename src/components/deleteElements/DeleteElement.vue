<template>
    <span @click="() => deleteItem(props.item.id)">
      {{ el }}
        <img alt="delete" src="@/assets/delete.svg" />
    </span>
</template>

<script setup>
import { ref, defineEmits, defineProps } from "vue";

const emit = defineEmits(['remove-item']);
const props = defineProps({item: Object});
const el = ref("");

const deleteItem = (itemId) => {
  emit('remove-item', itemId);
  console.log("delete row", itemId);
  el.value = "";
};

</script>

<style scoped>
img {
  width: 30px;
  height: 30px;
}
</style>