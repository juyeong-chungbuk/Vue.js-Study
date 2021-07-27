<template>
    <div v-if="모달창열렸니" class="black-bg">
      <div class="white-bg">
          <h4>{{ 원룸들[clicked].title }}</h4>
          <p>{{ 원룸들[clicked].content }}</p>
          <Discount/>
          <!-- <button @click="모달창열렸니 = false">닫기</button> -->
      </div>
    </div>
</template>

<script>
export default {
    name: 'Modal',
    props : {
        원룸들 : Array,
        clicked : Number,
        모달창열렸니 : Boolean,
    }
}
</script>

<style>

</style>