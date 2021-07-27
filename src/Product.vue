<template>
    <div v-for="(원룸,i) in 원룸들" :key="i">
        <img :src="원룸들[i].image" class="room-img">
            <h4 class="red" :style="스타일">{{ 원룸들[i].id+1 }}.
                {{ 원룸들[i].title }}</h4>
            <p>가격 :
                {{ 원룸들[i].price }}만원</p>
            <p>{{ 원룸들[i].content }}</p>
            <!-- <button @click="신고수[i]++">허위매물신고</button> -->
            <span>신고 수 :
                {{ 신고수[i] }}</span>
        </div>
</template>

<script>
export default {
    name : 'Product',
    props : {
        원룸들 : Array,
        신고수 : Array,
        모달창열렸니 : Boolean,
    }
}
</script>

<style>

</style>