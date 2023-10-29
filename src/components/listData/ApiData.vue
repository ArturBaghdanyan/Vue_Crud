<template>
  <form @submit.prevent="addColumn">
      <input type="text" v-model="text" />
      <button>add element</button>
  </form>
  <div v-for="item in list" :key="item.id" class="container">
    <span>
      {{ item.title }}
    </span>
    <div class="icons">
      <span @click="editMemberText">
        <img alt="Vue logo" src="@/assets/edit.svg" />
      </span>
      <DeleteElement @remove-item="removeItem" :item="item" />
    </div>
</div>
</template>

<script setup>
import { ref } from "vue";

import { v4 as uuidv4 } from "uuid";
import { data } from "@/data";
import DeleteElement from "@/components/deleteElements/DeleteElement.vue";
// import EditColumn from "@/components/editColumn/EditColumn.vue";

const text = ref("");
const list = ref(data);

const removeItem = (id) => {
  console.log(id)
  list.value = list.value.filter((item => item.id !== id));
};

const addColumn = () => {
  console.log("add row");
  if(list.value.length < 6) {
    list.value.push({
      id: uuidv4(),
      title: text.value
    });
  }   
};
</script>

<style scoped>
.container {
  width: 300px;
  height: auto;
  margin: auto;
  margin-top: 5px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 3px;
  border-bottom: 1px solid black;
}
img {
  width: 30px;
  height: 30px;
}
.icons {
  display: flex;
}

</style>