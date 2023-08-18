<template>
<div class="app">
  
  <header>
    <div class="title">
      <img src="./assets/heart.svg" alt="heart">
      <h1>Hello, Hyrule</h1>
    </div>
    <div class="order">
      
      <button @click="handleClick('title')">Order by title</button>
 <button @click="handleClick('salary')">Order by Salary</button>
 <button @click="handleClick('location') ">Order by Location</button>
    </div>
  </header>

<JobList :jobs="jobs" :order = "order" />

</div>
  
</template>

<script lang="ts">
import { defineComponent, reactive, ref , toRefs} from 'vue';
import Job from './types/Job'
import JobList from './components/JobList.vue';
import OrderTerm from './types/OrderTerm';


export default defineComponent({
  name: 'App',
  components: { JobList},
  setup() {
    /*
    const name = ref('Link');
    const age = ref<number | string>(25);


const state = reactive({name: "Link", age: 25 as string | number});

return {...toRefs(state)}
 
*/

const jobs = ref<Job[]>([
  {title: 'Farm Worker', location: 'lon lon ranch', salary:30000, id:'1' },
  { title: 'Fairy Healer', location: 'Fairy Fountain', salary: 35000, id: '2' },
  { title: 'Bomb Shop Clerk', location: 'Kakariko Village', salary: 28000, id: '3' },
  { title: 'Windmill Operator', location: 'Kakariko Village', salary: 25000, id: '4' },
  { title: 'Treasure Hunter', location: 'Hyrule Field', salary: 40000, id: '5' },
  { title: 'Fisherman', location: 'Lake Hylia', salary: 32000, id: '6' },
  { title: 'Temple Explorer', location: 'Lost Woods', salary: 45000, id: '7' },
  { title: 'Guard', location: 'Hyrule Castle', salary: 37000, id: '8' },
  { title: 'Potion Brewer', location: 'Kokiri Forest', salary: 34000, id: '9' },
  { title: 'Music Instructor', location: 'Ocarina School', salary: 36000, id: '10' },

]);

const order = ref<OrderTerm>('title');
const handleClick = (term: OrderTerm) => {
  order.value = term;
 

}

return {jobs, handleClick, order};



}});
</script>

<style>
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
    background: #ccedff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }

  button:hover {
    background: #a5e0ff;
  }

  header .title{
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
