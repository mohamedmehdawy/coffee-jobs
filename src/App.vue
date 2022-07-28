<script setup lang="ts">
import { reactive, ref } from "@vue/reactivity";
import { Job } from "./interfaces/Job";

const name = ref<number>(0);

const user: Job = reactive({
  id: "20",
  title: "mohamed",
  location: "hosh esa",
  salary: 344,
});
console.log(name);
</script>

<template>
  <section class="main-app">hello, {{ myName }}</section>
</template>

<style scoped></style>
