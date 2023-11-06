<template>
    <div class="max-w-6xl m-auto px-4">
        <h3 class=" text-3xl mb-6">Order By <span class="font-semibold"> {{ order }}</span></h3>
        <transition-group name="list" tag="ul">
            <li class="bg-white p-6 mb-4 transition-all shadow-lg hover:shadow-2xl" v-for="job in orderedJobs"
                :key="job.id">
                <h2 class="font-bold text-2xl">{{ job.title }} in {{ job.location }}</h2>
                <div class="py-3 text-green-600 font-bold text-xl flex items-center gap-2">
                    <img src="../assets/rupee.svg" class="w-7">
                    <p>{{ job.salary }} rupees</p>
                </div>
                <div>
                    <p class="text-gray-500">
                        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eaque aperiam in eos
                        animi placeat velit
                        esse consectetur doloremque aliquid. Quos harum ipsa pariatur ducimus, officia optio atque minima
                        quibusdam praesentium.
                    </p>
                </div>
            </li>
        </transition-group>
    </div>
</template>

<script lang="ts">
import Job from '@/types/job';
import OrderTerm from '@/types/OrderTerm';
import { computed, defineComponent, PropType } from 'vue';
export default defineComponent({
    props: {
        jobs: {
            required: true,
            type: Array as PropType<Job[]>
        },
        order: {
            required: true,
            type: String as PropType<OrderTerm>
        }
    },
    setup(props) {
        const orderedJobs = computed(() => {
            return [...props.jobs].sort((a: Job, b: Job) => {
                return a[props.order] > b[props.order] ? 1 : -1
            })
        })

        return { orderedJobs }
    }
});
</script>
<style>
.list-move {
    transition: all 1s;
}
</style>