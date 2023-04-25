<template>
  <div class="box">
    <h3>拖动下方滑块完成拼图</h3>
    <div class="img-box">
      <img class="bg" src="../assets/hycdn.jpeg" alt="">
      <img class="hd" src="../assets/hycdn.png" alt="">
    </div>
    <div class="btn-box">
      <div class="btn">|||</div>
    </div>
  </div>
  </template>
  
  <script setup>
import {reactive} from 'vue'
  </script>
  <style scoped>
  html,body {
    width: 100%;
    height: 100%;
    user-select: none;
  }
  .box{
    width: 340px;
    height: 300px;
    border: 1px solid #ccc;
    margin: 0 auto;
    padding: 10px;
  }
  .img-box{
    position: relative;
  }
  .bg{
    width: 100%;
  }
  .hd{
    position:absolute;
    height:68px ;
    width: 68px;
    left: 26px;
    cursor: pointer;
  }
  .btn-box {
    width: 100%;
    height:10px ;
    border-radius: 5px;
    background: #e4e4e4;
    margin-top: 15px;
  }
  .btn {
    position: relative;
    top:-10px;
    left: 10px;
    width: 55px;
    height: 30px;
    text-align: center;
    letter-spacing: 5px;
    line-height: 30px;
    color: #fff;
    border-radius: 15px;
    background-color: rgb(26, 121, 255);
    box-shadow: rgb(26 121 255 / 52%) 0px 0px 10px 1px;
    cursor: pointer;
  }
</style>