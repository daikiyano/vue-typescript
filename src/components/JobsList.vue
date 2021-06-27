<template>
  <div>
    <p>Ordered by {{ order }}</p>
    <ul>
      <li v-for="job in OrderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
      </li>
    </ul>
  </div>
</template>
<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>,
    },
  },
  setup(props) {
    const OrderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });
    return { OrderedJobs };
  },
});
</script>

<style scoped>
</style>
