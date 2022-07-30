<script setup lang="ts">
import { computed } from "@vue/reactivity";
import Job from "../../interfaces/Job";
import OrderTerm from "../../interfaces/OrderTerm";
const props = defineProps<{
    jobs: Job[];
    order: OrderTerm;
}>();

const orderedJobs = computed<Job[]>(() => {
    return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
    });
});
</script>
<template>
    <section class="job-list">
        <p>Orders by {{ order }}</p>
        <transition-group name="list" tag="ul">
            <li v-for="job in orderedJobs" :key="job.id">
                <h2>{{ job.title }} in {{ job.location }}</h2>
                <section class="salary">
                    <img src="../../assets/icons/rupee.svg" alt="rupee" />
                    <p>{{ job.salary }}</p>
                </section>
                <section class="description">
                    <p>
                        Lorem, ipsum dolor sit amet consectetur adipisicing
                        elit. Incidunt eos placeat quibusdam omnis, nihil
                        numquam. Eaque iusto laboriosam vero fuga quasi
                        corrupti, delectus maiores, quibusdam soluta quod sed
                        ullam a.
                    </p>
                </section>
            </li>
        </transition-group>
    </section>
</template>
<style scoped>
.job-list {
    max-width: 960px;
    margin: 40px auto;
}
.job-list ul {
    padding: 0;
}
.job-list li {
    list-style-type: none;
    background: white;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
}
.job-list h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
}
.salary {
    display: flex;
}
.salary img {
    width: 30px;
}
.salary p {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px;
}
.list-move {
    transition: all 1s;
}
</style>
