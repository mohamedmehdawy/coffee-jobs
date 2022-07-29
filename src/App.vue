<script setup lang="ts">
import { ref } from "@vue/reactivity";
import Job from "./interfaces/Job";
import OrderTerm from "./interfaces/OrderTerm";
import JobList from "./components/jobList/JobList.vue";

const jobs = ref<Job[]>([
    { title: "farm worker", location: "lon lon ranch", salary: 30000, id: "1" },
    { title: "quarryman", location: "death mountain", salary: 40000, id: "2" },
    {
        title: "flute player",
        location: "the lost woods",
        salary: 35000,
        id: "3",
    },
    { title: "fisherman", location: "lake hylia", salary: 21000, id: "4" },
    {
        title: "prison guard",
        location: "gerudo valley",
        salary: 32000,
        id: "5",
    },
]);

const orderList = ref<OrderTerm[]>(["title", "location", "salary"]);
const order = ref<OrderTerm>(orderList.value[0]);

function handelClick(term: OrderTerm): void {
    order.value = term;
}
</script>

<template>
    <section class="main-app">
        <header>
            <section class="order">
                <button @click="handelClick(order)" v-for="order in orderList" :key="order">Order by {{order}}</button>
            </section>
        </header>
        <JobList :jobs="jobs" :order="order"/>
    </section>
</template>

<style scoped>
header {
    text-align: center;
}
header .order {
    margin-top: 20px;
}
button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
}
</style>
