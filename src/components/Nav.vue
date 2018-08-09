<template>
    <nav class="nav" id="nav">
        <div id="logo" class="logo">
            <a href="javascript:void(0)" v-on:click="goToHome">
                <img v-bind:src="logoSrc" id="src" alt="慕课网">
            </a>
        </div>
        <ul class="nav-item">
            <li><a href="javascript:void(0)">免费课程</a></li>
            <li><a href="javascript:void(0)">职业路径</a></li>
            <li><a href="javascript:void(0)">实战</a></li>
            <li><a href="javascript:void(0)">猿问</a></li>
            <li><a href="javascript:void(0)">手记</a></li>
            <li><a href="javascript:void(0)">找工作<i class="icon-new"></i></a></li>
        </ul>
        <div class="search-area">
            <input type="text" class="search-input">
            <div class="search-all-tag">
                <a href="javascript:void(0)" class="search-tag">前端入门</a>
                <a href="javascript:void(0)" class="search-tag">Java入门</a>
                <a href="javascript:void(0)" class="search-btn"></a>
            </div>
        </div>
        <ul class="nav-unlogin">
            <li><a href="javascript:void(0)">下载APP</a></li>
            <li><a href="javascript:void(0)" class="shopping-car"> 购物车</a></li>
            <li><a href="javascript:void(0)">登录</a></li>
            <li><a href="javascript:void(0)" style="color: #d9dde1">/</a></li>
            <li><a href="javascript:void(0)">注册</a></li>
        </ul>
    </nav>
</template>

<script>
import '../../static/css/nav.css';

export default {
    props: ['logoSrc'],
    methods: {
        goToHome() {
            this.$router.push('/');
        }
    }
}
</script>



