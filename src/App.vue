<template>
<div><!--base-->
 

  <div class ='menu'>
    <a v-for="menu in menus" :key="menu">{{menu}}</a>
  </div>

  <div>
    <h4>{{products[0]}}</h4>
    <p>{{price}}만원</p>
    <button @click="신고수++">신고</button> <span>{{신고수}}</span>
  </div>
  <!-- -> Disscount.vue
  <div clss ="discount">
    <h4>지금 결제하면 20% 할인!</h4>
  </div>
  -->
  <transition name="fade">
  <Modal @해줘="modalopen = false;" :selected = 'selected' :원룸들 = '원룸들' :modalopen = "modalopen"/>
  </transition>
  <Discount/>

  <div class="databind" v-for="(room, i) in 원룸들" :key="i">
    <img :src="원룸들[i].image" class="room-img">
    <h4 @click="modalopen = true; selected = i">{{원룸들[i].title}}</h4>
    <p>{{원룸들[i].price}}</p>
  </div>


</div>
</template>

<script>

import roomdata from './assets/rooms.js';
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';
export default {
  name: 'App',
  data(){
      return{
        price:10,
        selected : 0,
        products:['원룸1','원룸2','원룸3'],
        menus:['Home', 'Shop', 'About'],
        modalopen: false,
        신고수 : 0,
        원룸들 : roomdata,
      }  
  },

  components: {
    Discount : Discount,
    Modal : Modal,
  }
}
</script>

<style>
.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: 1s;
}
.fade-enter-to {
  transform: translateY(0px);
}

.fade-leave-from {
  opacity:0;
}
.fade-leave-active {
  transition: 1s;
}
.fade-leave-to {
  opacity: 1;
}


.start{
  opacity:0;
  transition: all 1s;
}
.end{
  opacity: 1;
}
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
.discount{
  background : #eee;
  margin : 10px;
  padding: 10px;
  border-radius: 5px;
}

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
