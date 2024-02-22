<template>
  <div class="mx-5">
    <ul>
      <li v-for="job in orderJobs" :key="job.id" class="list-none bg-white p-3 my-3 rounded-md">
        <h2 class="capitalize mb-2">{{job.title}} in {{job.location}}</h2>
        <div class="flex">
          <p class="mb-2 font-bold text-blue-600">{{job.salary}} MMK</p>
        </div>
        <div class="description">
          <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's
            standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.
            It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages,
            and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import {computed, defineComponent, PropType} from 'vue'
import Job from "@/types/Job";
import job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
 props : {
   jobs : {
     required : true,
     type : Array as PropType<Job[]>
   },
   order : {
     required: true,
     type : String as PropType<OrderTerm>
   }
 },
  setup(props) {
    const orderJobs = computed(()=>{
      return [...props.jobs].sort((a:Job , b:Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })
    return {orderJobs}
  }
})
</script>

<style scoped>

</style>