<!-- vbase-3-setup -->
<template>
  <div>
    <!-- 1. 模板语法 （小胡子语法） -->
    {{ msg }}

    <!-- 2. 指令 -->

    <!-- v-text 模板语法: 渲染纯文本 -->
    <div v-text="htmlStr"></div>

    <!-- v-html 模板语法: 渲染HTML标签 -->
    <div v-html="htmlStr"></div>

    <!-- v-model 双向绑定: 输入框的值 -->
    <input type="text" v-model="msg">

    <!-- v-bind 动态属性, 只要属性加了v-bind:就可以解析变量,  v-bind简写成: -->
    <!-- <img v-bind:src="imgSrc" alt=""> -->
    <img style="width: 230px;" :src="imgSrc" alt="">

    <!-- v-if 条件渲染: 布尔值, true显示，false隐藏-->
    <div v-if="isShow">你可以看到我？</div>

    <!-- v-for="(数组的每一项,数组的下标) of 数组" -->
    <div v-for="(item, index) of arr"> {{ index }}: {{ item }} </div>

    <!-- @事件名="事件处理程序" -->
    <div @click="fn1">点击我</div>

  </div>
</template>

<script setup>
// 导入数据响应模块
import { reactive, ref } from 'vue';

// 变量：存储数据的容器 （可以改变的量）,  var或者let声明
// 常量：只读变量 （不可以改变的量）, const声明


// 基本类型变量： 123  "abc"   true,false   null  undefined  需要ref()数据响应模块
const msg = ref("你好世界");
const htmlStr = ref("<h1>这是一个大标题标签</h1>");
const imgSrc = ref("https://desk-fd.zol-img.com.cn/t_s960x600c5/g7/M00/02/04/ChMkLGJ11T6ILC4hABchN71447wAADI1wPjd-8AFyFP259.jpg");
const isShow = ref(true);

// 引用类型变量:  数组[1,2,3]   对象{name: "小帅"}   需要reactive()数据响应模块
const arr = reactive(["误杀3", "海上钢琴师", "这个杀手不太冷", "阿甘正传", "华尔街之狼"]);


// 定义函数
function fn1() {
  console.log("点击了div");

  // 修改msg的值
  msg.value = "hello world";
  // 获取msg的值
  console.log(msg.value);

  // 修改isShow的值
  isShow.value = false;

  // 修改数组的某一项下标
  arr[4] = "猫鼠游戏";
}
</script>

<style lang="scss" scoped></style>