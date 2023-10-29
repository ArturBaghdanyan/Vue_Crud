<template>
    <span @click="editMemberText(id, 'New Title')">
        <img alt="Vue logo" src="@/assets/edit.svg" />
    </span>
</template>

<script setup>
import { data } from "@/data";
import { ref } from 'vue';

const updatedCards = ref([...data]);

const editMemberText = (id, title) => {
console.log("update", id, title);
updatedCards.value = updatedCards.value.map(item => {
    if (item.id === id) {
    return {
        ...item,
        title,
    };
    }
    return item;
});
};
</script>

<style scoped>
img {
  width: 30px;
  height: 30px;
}
</style>