//Modal.vue

<template>
  <div class="black-bg" v-if="모달창">
    <div class="white-bg">
      <img :src="원룸들[상품번호].image" class="room-image" />
      <h4>{{ 원룸들[상품번호].title }}</h4>
      <p>{{ 원룸들[상품번호].content }}</p>
      <input v-model="month">
      <p> {{ month }} 개월 선택함 : {{ 원룸들[상품번호].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  data(){
    return {
      month : 1,
    }
  },  
  props:{
    원룸들 : Array,
    상품번호 : Number,
    모달창 : Boolean
  },
  watch : {
    month(a){
      if (isNaN(a) == true){
        alert('문자입력하지마세요');
        this.month = 1;
      }
      if(a<1 || a>12){
        alert('1개월 이상 12개월 이하로 입력해주세요');
        this.month = 1;
      }
    },
 },
beforeUpdate() {
    if (this.month == 2) {
      alert('2개월은 너무 적음.. 안팝니다');
      this.month = 1;}
  }
  
}
</script>