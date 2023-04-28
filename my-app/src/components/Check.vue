<template>
  <div class="box">
    <h3>拖动下方的图片完成拼图</h3>
    <div ref="bgImgRef" class="img-box">
      <img class="bg" src="../assets/hycdn.jpeg" alt="">
      <img 
      class="hd" 
      :style="{ left:data.left + 'px' , top:data.top + 'px'}"
      src="../assets/hycdn.png" 
      alt="">
    </div>
    <div class="btn-box">
      <div :style="{left:data.left + 'px'}"  ref="btnRef" class="btn" @mousedown="btnMousedown">|||</div>
    </div>
  </div>
</template>

<script setup>
import { reactive, onMounted, toRefs ,ref} from "vue";
 
let $props = defineProps({
  top:{
    type:Number,
    default:45
  }
})

let $emit = defineEmits(['getPosition'])

const data = reactive({
  left:28,
  top:$props.top,
  btnLeft:0,
  btnRef:null,
  offsetLeft: 0,
  bgImgRef:null,
});
const { btnRef,bgImgRef } = toRefs(data);

onMounted(()=>{
  data.offsetLeft = data.bgImgRef.offsetLeft
  console.log('xxx');
  document.body.addEventListener('mouseup' , btnMouseup)

})

// 按下
var btnMousedown = (e)=>{
  // 鼠标按下计算出鼠标的位置
  data.btnLeft = e.pageX - data.btnRef.offsetLeft
  document.body.addEventListener('mousemove' , btnMousemove)
}
// 滑动的时候子要求鼠标没有松开
var btnMousemove = (e)=>{
  // console.log('滑动');
  // left表示小图片的位置
  let x = e.pageX - data.offsetLeft - data.btnLeft;
  if(x <= 0) x = 0;
  else if(x >= 285) x = 285;
 
  data.left = x;
}
// 松开鼠标
var btnMouseup = (e)=>{
  // console.log(data.left);
  $emit('getPosition' , data.left)
  // 移出帮定的移动事件
  document.body.removeEventListener('mousemove',btnMousemove)
}
</script>
<style scoped>
html,
body {
  width: 100%;
  height: 100%;
  user-select: none;
}
.box {
  width: 340px;
  height: 300px;
  border: 1px solid #ccc;
  margin: 0 auto;
  padding: 10px;
}
.img-box {
  position: relative;
}
.bg {
  width: 100%;
}
.hd {
  position: absolute;
  height: 68px;
  width: 68px;
  /* top: 45px; */
  left: 26px;
  cursor: pointer;
}
.btn-box {
  width: 100%;
  height: 10px;
  border-radius: 5px;
  background: #e4e4e4;
  margin-top: 15px;
}
.btn {
  position: relative;
  top: -10px;
  left: 26px;
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