<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo" />
        <h1>Hyrule jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobsList.vue";
import jobData from "./data/jobs.json";
import type { Job, OrderTerm } from "./types";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>(jobData);
    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, order, handleClick };
  },
});
</script>

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
header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
</style>
