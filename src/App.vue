<template>
    <Modal :원룸들="원룸들" :clicked="clicked" :모달창열렸니="모달창열렸니" />

    <div class="menu">
        <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
        <!-- <a href="">Products</a> <a href="">About</a> -->
    </div>

    <Discount/>
    <Product :원룸들="원룸들" :신고수="신고수" :모달창열렸니="모달창열렸니"/>

    <!-- <div v-for="(원룸,i) in 원룸들" :key="i">
        <img :src="원룸들[i].image" class="room-img">
            <h4 @click="모달창열렸니 = true; clicked = i" class="red" :style="스타일">{{ 원룸들[i].id+1 }}.
                {{ 원룸들[i].title }}</h4>
            <p>가격 :
                {{ 원룸들[i].price }}만원</p>
            <p>{{ 원룸들[i].content }}</p>
            <button @click="신고수[i]++">허위매물신고</button>
            <span>신고 수 :
                {{ 신고수[i] }}</span>
        </div> -->
</template>

<script>
  // let array = [10,20,30]; 
  // array[1] html에서 배열 출력 법
  import data from './assets/oneroom.js'; // .js는 생략가능
  import Discount from './Discount.vue';
  import Modal from './Modal.vue';
  import Product from './Product.vue';

  export default {
      name: 'App',
      data() {    // 데이터 보관하는 법
        return {
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
        Product : Product,
      }
  } // data, methods, components 각각 따로 있는 구조임
</script>

<style>
  body{
    margin: 0;
  }
  div {
    box-sizing: border-box;
  }
  /* .discount{
    background: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
  } */
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