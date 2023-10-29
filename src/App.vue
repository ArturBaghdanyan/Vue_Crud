<template>
  <ApiData />
  <GetData />
</template>

<script>
import ApiData from "@/components/listData/ApiData.vue";
import GetData from "@/apiLists/GetData.vue";

export default {
  name: 'App',
  components: {
    ApiData,
    GetData,
  },
  props: {
    item: Object
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
