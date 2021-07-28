<template>
    <div class="discount">
      <h4>지금 결제하면 {{ sale }}% 할인</h4>
    </div>
</template>

<script>
export default {
    name: 'Discount',
    data(){
      return{
        sale : 20,
      }
    },
    mounted(){
      setInterval(()=>{  
        if(this.sale > 0)
          this.sale -= 2;
        else
        this.sale = 20;
      },1000);
    }          
}
</script>

<style>
 .discount{
    background: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
  }
</style>