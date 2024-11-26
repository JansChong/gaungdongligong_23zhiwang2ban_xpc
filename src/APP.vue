<!-- vbase-3-setup -->
<template>
    <div>
        <img v-for="item of doutu.arr" :src="item" alt="">
    </div>
</template>

<script setup>
// 导入axios网络请求模块
import axios from "axios";
import {reactive} from "vue";

// 声明一个斗图变量（响应式的变量）
const doutu = reactive({
    arr: [ ]
})

// axios(配置)  配置是一个对象
axios({
    // 请求地址(接口地址)
    // url: "https://v2.alapi.cn/api/qinghua",
    url: "https://v2.alapi.cn/api/doutu",

    // 请求方式
    method: "GET",

    // 请求参数  data(用于POST请求)  params(用于GET请求)
    params: {
        token: "v9H3VS4QquA2VhM3",
        // format: "json"
        keyword: "小黑子"
    },
})
    // 请求成功执行 then方法
    .then(res => {
        console.log("请求成功 =>", res.data.data);

        // 把网络请求到的表情包，赋值给变量
        doutu.arr = res.data.data;
    })
    // 请求失败执行 catch方法
    .catch(err => {
        console.log("失败原因 =>", err);
    })

</script>


<style lang="scss" scoped></style>
