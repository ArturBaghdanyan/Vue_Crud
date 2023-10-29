<!-- <template>
    <span @click="editMemberText">
      <img alt="Vue logo" src="@/assets/edit.svg" />
    </span>
</template>

<script setup>
import { data } from "@/data";

const editMemberText = (id, title) => {
console.log("a", id, title)
const updatedCards = data.map(item => {
    if (item.id === id) {
    return {
        ...item,
        title,
    };
    }
    return item;
});
updatedCards();
};
</script> -->