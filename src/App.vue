<!-- Composition API -->



<script setup>

import { ref , onMounted} from 'vue';
// export default {
//   setup() {
    const name=ref('Shadab Haidri');
    const status=ref('active');
    const tasks=ref(['Suhoor','Study','Bath','Sleep','Iftar']);
    const newTask=ref('');

    const addTask=()=>{
      if(newTask.value.trim()!== ''){
         tasks.value.push(newTask.value);
         newTask.value='';
      }
    };

    const deleteTask=(index)=>{
      console.log(index);
      tasks.value.splice(index,1);
    };


    const toggleStatus=()=>{
      
      if(status.value==='active'){
        status.value='pending';
      }else if(status.value==='pending'){
        status.value='inactive'
      }else{
        status.value='active';
      }
    }

    // return{
    // name,
    // status,
    // tasks,
    // toggleStatus,
    // }
//   },
// };

onMounted(async ()=>{
  try {
    const response = await fetch ('https://jsonplaceholder.typicode.com/todos');
    const data=await response.json();
    tasks.value=data.map((task)=>
      task.title);
  } catch (error) {
    console.log("Error fetching API",error);
  }
})

</script>



<template>
  <h1>Hello <span>{{ name }}</span></h1>

  <p v-if="status==='active'">User is Active</p>
  <p v-else-if="status==='pending'">User is pending</p>
  <p v-else>User is Inactive</p>

  <p>Hello Daniel</p>

  <form @submit.prevent="addTask()">
    <label for="newTask"> Add Task</label>
    <input type="text" name="newtask" id="newTask" v-model="newTask">
    <button type="submit" >Add Task</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task,index) in tasks":key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>
  
  <br/>
  <!-- <button v-on:click="toggleStatus">Click for Change Status</button> -->
   <!-- Another way to add functionality -->
  <button @click="toggleStatus">Click for Change Status</button>

</template>




<style scoped>
p{
  background-color: red;
  width: 100px;
  height: 100px;
}
 h1{
  color: red;
  height:60px;
  width:60px;
  padding: 60px;
  background-color:rgb(194, 158, 158) ;
  margin:auto;
 }
 li{
  list-style: none;
 }
</style>
