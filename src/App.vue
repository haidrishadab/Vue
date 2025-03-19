<script>
export default{
  data(){
    return{
      name:'Shadab Haidri',
      status:'pending',
    };
  },
};
</script>



<template>
  <h1>Hello <span>{{ name }}</span></h1>
  <p v-if="status==='active'">User is Active</p>
  <p v-else-if="status==='pending'">User is pending</p>
  <p v-else>User is inactive</p>
  <p>Hello Daniel</p>
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
</style>
