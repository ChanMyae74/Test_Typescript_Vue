<template>
<div id="app">
  <header class="text-center mt-3">
    <div>
      <h1 class="text-[47px] text-white">JobList</h1>
    </div>
    <button @click="handleClick('title')" class="mx-2 px-3 bg-white rounded-md cursor-pointer">order by title</button>
    <button @click="handleClick('location')" class="mx-2 px-3 bg-white rounded-md cursor-pointer">order by location</button>
    <button @click="handleClick('salary')" class="mx-2 px-3 bg-white rounded-md cursor-pointer">order by salary</button>
  </header>
  <JobList :jobs="jobs" :order="order"></JobList>
</div>
</template>

<script lang="ts">
import {defineComponent, ref} from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import Job from "./types/Job";
import JobList from "@/components/JobList.vue";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  name: 'App',
  components: {
    JobList
  },
  // data() {
  //   return {
  //     name : 'Link',
  //     age : 27 as number | string
  //   }
  // },
  setup() {
    // const name = ref('Link');
    // const age = ref<string|number>(27);
    // return {name , age}
    const jobs = ref<Job[]>([
      { title : 'Web Developer', location : "Yangon", salary : 500000, id : '1'},
      { title : 'Mid Web Developer', location : "Yangon", salary : 700000, id : '2'},
      { title : 'Senior Web Developer', location : "Yangon", salary : 1500000, id : '3'},
      { title : 'Full Stack Web Developer', location : "Yangon", salary : 1500000, id : '4'},
      { title : 'Java Developer', location : "Yangon", salary : 1500000, id : '5'},
    ])

    const order = ref<OrderTerm>('title')
    const handleClick = (term : OrderTerm) => {
          order.value = term
    }
    return {jobs,handleClick,order };
  },
  methods : {
    // changeName (name :string) {
    //     this.name = name
    //   return name
    // },
    // changeAge (age :string | number) {
    //   this.age = age
    //   return age
    // }
  }
});
</script>

<style>

</style>
