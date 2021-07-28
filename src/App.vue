<template>
  <transition name="fade">
     <Modal @closeModal="모달창열렸니=false" 
     :원룸들="원룸들" :clicked="clicked" 
     :모달창열렸니="모달창열렸니" />
  </transition>
  <!-- <div class="start" :class="{ end : 모달창열렸니 }">
    <Modal @closeModal="모달창열렸니=false" :원룸들="원룸들" :clicked="clicked" :모달창열렸니="모달창열렸니" />
  </div> -->
    <div class="menu">
        <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
        <!-- <a href="">Products</a> <a href="">About</a> -->
    </div>

    <Discount :이름="오브젝트.name" :나미="오브젝트.age" />
    <Card @openModal="모달창열렸니=true; clicked=$event" :원룸="원룸들[i]" v-for="(원룸,i) in 원룸들" :key="i" />
</template>

<script>
  import data from './assets/oneroom.js'; // .js는 생략가능
  import Discount from './Discount.vue';
  import Modal from './Modal.vue';
  import Card from './Card.vue';

  export default {
      name: 'App',
      data() {    // 데이터 보관하는 법
        return {
          오브젝트 : { name : 'Kim', age : 20 },
          clicked: 0,
          원룸들 : data,
          모달창열렸니 : false, // 모달창의 현재 상태를 보관하는 데이터 - 닫힌상태 or 열린상태
          price1: 60,
          price2: 70,
          스타일: 'color : blue',
          products: [
              '역삼동원룸', '천호동원룸', '마포구원룸'
          ],
          menus: ['Home', 'Products', 'About'],
          신고수 : [0,0,0,0,0,0],
        }  
      },
      methods : {   // 함수 만드는 공간
        increase(){
          this.신고수+= 1;
        },
      },
      components: {
        Discount : Discount, // 같은 이름으로 쓸거면 Discount 하나만 써도 가능
        Modal : Modal,
        Card : Card,
      }
  } // data, methods, components 각각 따로 있는 구조임
</script>

<style>
  /* .start{
    opacity: 0;
    transition: all 1s; 
  }
  .end{
    opacity: 1;
  } */
  /* 시작 시 스타일 */
  .fade-enter-from{
    opacity: 0;
  }
  /*  */
  .fade-enter-active{
    transition: all 1s;
  }
  /* 끝날 시 스타일 */
  .fade-enter-to{
    opacity: 1;
  }
  body{
    margin: 0;
  }
  div {
    box-sizing: border-box;
  }
  .discount{
    background: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
  }
  .black-bg{
    width: 100%; height: 100%;
    background: rgba(0, 0, 0, 0.5);
    position: fixed; padding: 20px;
  }
  .white-bg{
    width: 100%; background: white;
    border-radius: 8px;
    padding: 20px;
  }
  .room-img{
    width: 100%;
    margin-top: 40px;
  }
  #app {
      font-family: Avenir, Helvetica, Arial, sans-serif;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      text-align: center;
      color: #2c3e50;
  }
  .menu {
      background: darkslateblue;
      padding: 15px;
      border-radius: 5px;
  }
  .menu a {
      color: white;
      padding: 10px;
  }
</style>