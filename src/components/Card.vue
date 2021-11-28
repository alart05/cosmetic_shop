<template>
  <div class='card'>
    <img class="image" :src='item.image_link'>
    <div class='text'>{{ item.name }}</div>
    <div class='price'>${{ item.price }}</div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    item: { type: Object }
  }
}
</script>

<style lang="scss" scoped>
  .image{
    width: 100%;
    margin: auto;  
    display: flex;
  }
  .text{
    text-align: center;
    color: #19191D;
  }
  .card{
    border: 1px solid #9DC2FF;
    box-sizing: border-box;
    border-radius: 10px;
    padding-bottom: 10px;
    cursor: pointer;
  }
  .card:hover {
    box-shadow: 6px 24px 34px rgb(0 0 0 / 10%), 3px 9px 14px rgb(0 0 0 / 9%);
}
  .button{
    border: 1px solid #9DC2FF;
    box-sizing: border-box;
    border-radius: 8px;
    width: 88px;
    height: 32px;
    color: #2264D1;
  }
  .price{
    margin-top: 7px;
    text-align: center;
    font-weight: bold;
    font-size: 24px;
    color:#000000;
    padding-top: 10px;
  }
</style>