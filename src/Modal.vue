<template>
    <div v-if="모달창열렸니" class="black-bg">
      <div class="white-bg">

          <h4>{{ 원룸들[clicked].title }}</h4>
          <p>{{ 원룸들[clicked].content }}</p>
          <p>{{ 원룸들[clicked].price }}</p>
          <Discount/>

          <!-- <textarea v-model="month"></textarea><br>
          <select v-model="month">
              <option value="month">{{month}}</option>
            </select>
            <br> -->
          <input @input="month = $event.target.value" type="text"><br>
          <!-- <input v-model.number="month" type="text"> -->
          <!-- <input type="range" min="1" max="12" > -->
          <p>{{ month }}개월 선택함 : {{원룸들[clicked].price * month }}원</p>
          <button @click="$emit('closeModal')">닫기</button>

      </div>
    </div>
</template>

<script>
import Discount from './Discount.vue';

export default {
    name: 'Modal',
    data(){
        return{
            month : 1,
        }
    },
    watch : {
        month(a){    //사용자가 month를 글자로 입력하면 경고문 띄워주기
            // if(a >= 13)
            //     alert('13개월은 안팔아요~!');
            const regExp = /[0-9]/g;
            if(!regExp.test(a)){
                alert('숫자를 입력해줘');
                this.month = 1;
            }
        },
    },
    props : {
        원룸들 : Array,
        clicked : Number,
        모달창열렸니 : Boolean,
    },
    component : {
        Discount : Discount,
    }
}
</script>

<style>

</style>