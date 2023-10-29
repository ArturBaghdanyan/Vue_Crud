<template>
  <div>
    <button @click="list = !list">open list</button>
    <ul v-if="list">
      <li v-for="item in urlData" :key="item.id">
        {{item.id}} : {{ item.title }}
      </li>
    </ul>
    <PostData @todo="addToList"/>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import PostData from "@/apiLists/PostRequest.vue";

const urlData = ref([]);
const error = ref(false)
const list = ref(false);

const addToList = (todo) => {
  return urlData.value.push(todo)
}

const getList = async () => {
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts');
      const data = await response.json();
      urlData.value = data; 
    } catch(err) {
      error.value = true;
      console.error(err);
      throw err;
    }
  } 

onMounted(() => {
  getList();
})
</script>