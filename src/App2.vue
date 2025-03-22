<!-- Option API -->


<script >
export default{
  data(){
    return{
      name:'Shadab Haidri',
      status:'pending',
      tasks:['Bath','Study','Suhoor','Iftar'],
      link:'https://google.com'
    };

  },
  methods:{
    toggleStatus(){
      if(this.status==='active'){
        this.status='pending';
      }else if(this.status==='pending'){
        this.status='inactive'
      }else{
        this.status='active';
      }
    }
  }
};
</script>



<template>
  <h1>Hello <span>{{ name }}</span></h1>
  <p v-if="status==='active'">User is Active</p>
  <p v-else-if="status==='pending'">User is pending</p>
  <p v-else>User is Inactive</p>
  <p>Hello Daniel</p>
  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks":key="task">{{ task }}</li>
  </ul>
  <!-- <a v-bind:href="link">Click for Google</a> -->
   <!-- there is another way of binding -->
  <a :href="link">Click for Google</a>
  <br/>
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
  background-color:black ;
  margin:auto;
 }
 li{
  list-style: none;
 }
</style>
