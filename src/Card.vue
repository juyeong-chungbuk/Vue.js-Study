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
    }
}
</script>

<style>

</style>