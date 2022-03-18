<template>
<div><!--base-->
  <!--modal  UI-->
  <div class="black-bg" v-if="modalopen">
    <div class="white-bg">
      <h4>제목</h4>
      <p>내용</p>
    </div>
  </div>

  <div class ='menu'>
    <a v-for="menu in menus" :key="menu">{{menu}}</a>

  </div>
  <div>
    <h4>{{products[0]}}</h4>
    <p>{{price}}만원</p>
    <button @click="신고수++">신고</button> <span>{{신고수}}</span>
  </div>
  <div class="databind">
    <img :src="원룸들[0].image" class="room-img">
    <h4>{{원룸들[0].title}}</h4>
    <p>{{원룸들[0].price}}</p>
  </div>

</div>
</template>

<script>

import roomdata from './assets/rooms.js';


export default {
  name: 'App',
  data(){
      return{
        price:10,
        products:['원룸1','원룸2','원룸3'],
        menus:['Home', 'Shop', 'About'],
        modalopen: false,
        신고수 : 0,
        원룸들 : roomdata
      }  
  },

  components: {

  }
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
}
body{margin:0}
div{box-sizing: border-box;}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width:100%;
  background: white;
  padding: 20px;
  border-radius: 5px;
}
.menu{
  background: #2c3e50;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color:white;
  padding: 10px;
}
</style>
