
//App.vue
<template>
  <transition name="fade">
    <Modal @closeModal="모달창 = false" :원룸들="원룸들" :상품번호="상품번호" :모달창="모달창"/>
  </transition>

  <div class="app">
    <nav class="menu">
      <a v-for="(작명1,작명2) in 메뉴들" :key="작명2">{{작명1}}</a>
    </nav>
    <Discount :amount="amount" v-if="showDiscount"/>

    <button @click="priceSortAsc"> 가격 오름차순 정렬</button> 
    <button @click="priceSortDesc"> 가격 내림차순 정렬</button>
    <button @click="nameSortAsc"> 상품명 가나다순 정렬</button>
    <button @click="nameSortDesc"> 상품명 가나다 역순 정렬</button>
    <button @click="sortBack"> 되돌리기 </button>

    <Card @openModal="모달창 = true; 상품번호=$event" :room="원룸들[index]" v-for="(원룸, index) in 원룸들" :key="index"/>
  </div>
</template>

<script>

import data from './assets/oneroom';
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';
import Card from './components/Card.vue';

export default {
  name : 'App',
  data(){
    return {
      amount : 30,
      showDiscount : true,
      원룸들오리지널 : [...data],
      상품번호 : 0,
      원룸들 : data,
      모달창 : false,
      신고수 : [0,0,0,0,0,0],
      메뉴들 : ['Home', 'Shop', 'About'],
      price1 : 100,
      price2 : 200,
      price3 : 300,
      products : ['해운대원룸', '에코델타시티원룸', '광안리원룸'],
    }
  },
  methods : {
    increase(){
      this.신고수 += 1;
    },
    priceSortAsc(){
      this.원룸들.sort((a, b) => a.price - b.price);
    },
    priceSortDesc(){
      this.원룸들.sort((a, b) => b.price - a.price);
    },
    nameSortAsc(){
      this.원룸들.sort((a, b) => a.title.localeCompare(b.title));
    },
    nameSortDesc(){
      this.원룸들.sort((a, b) => b.title.localeCompare(a.title));
    },
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
    },
  },
  components : {
    Discount,
    Modal,
    Card,
  },
  mounted(){
  setInterval(()=>{
      this.amount--;
  }, 1000);
  }
}
</script>