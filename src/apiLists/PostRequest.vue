<template>
	<div>
		<form @submit.prevent="postList">
			<input type="text" placeholder="Enter a title" v-model="inputValue" />
			<button type="submit">Add Post</button>
		</form>
		<ul v-if="show">
			<li v-for="item in posts" :key="item.id">
				{{ item.title }}
			</li>
		</ul>
	</div>
</template>
  
<script setup>
import { ref, defineEmits } from "vue";
const emit = defineEmits(['todo']);

const posts = ref([]);
const error = ref(false);
const show = ref(false);
const inputValue = ref('');

const postList = async () => {
	try {
		const response = await fetch("https://jsonplaceholder.typicode.com/posts", {
			method: "POST",
			headers: {
				"Content-type": "application/json",
			},
			body: JSON.stringify({
				userId: 1,
				body: inputValue.value,
				title: inputValue.value,
			}),
		});
		if (!response.ok) {
			throw new Error("Failed to add post");
		}
		const newPost = await response.json();
		emit('todo', newPost);
		console.log("Success", newPost);
		} catch (err) {
			console.error("Error", err);
			error.value = true;
		}
	};

</script>