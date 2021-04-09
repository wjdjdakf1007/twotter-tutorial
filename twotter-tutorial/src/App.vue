<template>
  <div id="app">
    @{{user.userName}} -{{fullName}}
    <strong>Followers:</strong>{{followers}}
    <button @click="followerUser"> Follow</button>
  </div>
</template>


<script>

export default{
 name:'App',   
 data() {
   return {
     followers:0,
     user:{
      id:1,
      userName:'kim',
      firstName:'ki',
      lastName:'m',
      email:'wjdjdakf17',
      isadmin:true
     },

   }
 },
 //마운트는 컴포넌트가 처음로드 될때마다 실행  콘솔로그랑 비슷하게 생각해도 된다. 로드되자마자 실행
 mounted() {
   this.followerUser();
 },
 watch:{
   followers(newFollowerCount, oldFollowerCount){
     if(oldFollowerCount < newFollowerCount){
       console.log(`${this.user.userName} has gained a follower!`)
     }
   }
 },
 methods: {
   followerUser(){
     this.followers++
   }
 },
 computed:{
   fullName(){
     return `${this.user.firstName}`
   }
 },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
}
</style>
