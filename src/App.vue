<template>
  <div class="app">
    <button @click="handleClick('title')">order by title</button>
    <button @click="handleClick('salary')">order by salary</button>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobsList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    // const state = reactive({
    //   name: "Link",
    //   age: 25 as string | number,
    // });
    // // state.name = 999 // cannot change type
    // state.age = 26;
    // return { ...toRefs(state) };
    // const name = ref("Link");
    // const age = ref<number | string>(25);
    // return { name, age };
    const jobs = ref<Job[]>([
      { title: "form worker", location: "london", salary: 12000, id: "1" },
      { title: "it worker", location: "tokyo", salary: 12000, id: "2" },
      { title: "factory worker", location: "london", salary: 12000, id: "3" },
      { title: "police worker", location: "london", salary: 12000, id: "4" },
      { title: "home worker", location: "london", salary: 12000, id: "5" },
    ]);
    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
      console.log(order.value);
    };
    return { jobs, handleClick, order };
  },
  // data() {
  //   return {
  //     name: "Link",
  //     age: 25 as number | string,
  //   };
  // },
});
</script>

<style>
</style>
