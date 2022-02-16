<template>
   <!--modal  UI-->
  <div class="black-bg" v-if="modalopen">
    <div class="white-bg">
      <h4>{{원룸들[selected].title}}</h4>
      <p>{{원룸들[selected].content}}</p>
      <input v-model = "amount">
      <select @input = "amount = $event.target.value">
          <option>6</option>
          <option>12</option>
          <option>24</option>
      </select>
      <p>{{amount}}개월 선택함 : {{원룸들[selected].price*amount}}</p>

      <p>가격: {{원룸들[selected].price}}</p>
      <button @click ="$emit('해줘')">닫기</button>
    </div>

  </div>
</template>

<script>
export default {
    name : 'Modal',
    data(){return{
        amount : 0,
    }
    },
    props : {
        원룸들 : Array,
        selected : Number,
        modalopen : Boolean,
    },
    watch : {
        amount(after){
            if((typeof after) !== "number" ){alert("숫자만 입력");}
        },
    }
}
</script>

<style>

</style>