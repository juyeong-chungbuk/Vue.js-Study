<template>
    <div>
        <img :src="원룸.image" class="room-img">
            <h4 @click="$emit('openModal', 원룸.id)">{{ 원룸.id+1 }}.
                {{ 원룸.title }}</h4>
            <p>가격 :
                {{ 원룸.price }}만원</p>
            <p>{{ 원룸.content }}</p>
            <!-- <button @click="신고수[i]++">허위매물신고</button> -->
            <!-- <span>신고 수 :
                {{ 신고수[i] }}</span> -->
        </div>
</template>

<script>
export default {
    name : 'Product',
    props : {
        원룸 : Object,
    },
    methods : {
        함수(){
            this.$emit('openModal', this.원룸.id) //emit을 함수안에서 하고싶으면
        }   //데이터를 함수안에서 참조할 때는 this 필수!
    }
}
</script>

<style>

</style>