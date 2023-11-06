<template>
  <div class="min-h-screen bg-slate-100 py-14">
    <div class="py-10 flex justify-center items-center gap-4">
      <img src="./assets/heart.svg" class=" w-28">
      <h1 class="text-5xl">Hyrule Jobs</h1>
    </div>
    <div class="max-w-5xl m-auto flex gap-3 mb-6 justify-center">
      <button class="py-2 md:px-6 px-2 bg-[#1195c9] text-white rounded-lg" @click="handleClcik('title')">Order by
        title</button>
      <button class="py-2 md:px-6 px-2 bg-[#1195c9] text-white rounded-lg" @click="handleClcik('salary')">Order by
        salary</button>
      <button class="py-2 md:px-6 px-2 bg-[#1195c9] text-white rounded-lg" @click="handleClcik('location')">Order by
        location</button>
    </div>
    <JobListVue :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/job'
import OrderTerm from './types/OrderTerm'
import JobListVue from './components/JobList.vue';
export default defineComponent({
  name: 'App',
  components: { JobListVue },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
      { title: 'quarryman', location: 'death mountain', salary: 50000, id: '2' },
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' },
    ])

    const order = ref<OrderTerm>('title')

    const handleClcik = (term: OrderTerm) => {
      order.value = term
    }
    return { jobs, handleClcik, order }
  },
});
</script>

<style></style>
