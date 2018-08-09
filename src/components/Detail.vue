<template>
    <div class="container">
        <div class="head-cover-container">
            <div class="box head-box">
                <div class="path">
                    <span v-text="course.path1"></span> \
                    <span v-text="course.path2"></span> \
                    <span v-text="course.path3"></span> \
                    <span v-text="course.path4"></span>
                </div>
                <h2 class="title" v-text="course.name"></h2>
                <div>
                    <div class="course-info">
                        <img v-bind:src="course.src" class="ct">
                        <span class="ct-detail"><a href="javascript:void(0)">{{course.teacherName}}&emsp;</a></span>
                    </div>
                    <div class="static-item"><span>难度</span> {{course.level}}</div>
                    <div class="static-item"><span>时长</span> {{course.time}}</div>
                    <div class="static-item"><span>学习人数</span> {{course.count}}</div>
                    <div class="static-item"><span>综合评分</span> {{course.score}}</div>
                </div>
            </div>
        </div>
        <div class="course-menu-container">
            <ul class="course-menu-box box">
                <li class="course-menu course-menu-sl">课程章节</li>
                <li class="course-menu">问答评论</li>
                <li class="course-menu">同学笔记</li>
                <li class="course-menu">问答评价</li>
            </ul>
        </div>
        <div class="content-container">
            <div class="content-box box">
                <div class="course-content">
                    <div class="course-desc">
                        简介：{{course.introduce}}
                    </div>
                    <div class="course-section" v-for="(item, index) in course.chapter" v-bind:key="index">
                        <h3 class="section-name">第{{index + 1}}章 {{item.title}}</h3>
                        <p class="section-desc">{{item.introduce}}</p>
                        <ul class="section-details">
                            <li class="section-detail" v-for="(item1, index1) in item.item" v-bind:key="index1">
                               <a href="javascript:void(0)">&emsp;{{index + 1}}-{{index1 + 1}} {{item1.name}} ({{item1.time}})</a>
                            </li>
                        </ul>
                    </div>
                </div>
                <div class="add-content">
                    <div class="course-card1">
                        <a class="begin-study" href="javascript:void(0)">开始学习</a>
                        <h5 class="card-title">课程须知</h5>
                        <p class="card-desc">{{course.basic}}</p>
                        <h5 class="card-title">老师能教你什么</h5>
                        <p class="card-desc">{{course.learn}}</p>
                    </div>
                    <div class="right-content-1">
                        <p class="add-title-1">推荐课程</p>
                        <ul>
                            <li class="one-re-course" v-for="(item, index) in reCourse" v-bind:key="index">
                                <img v-bind:src="item.img">
                                <p class="one-re-course-tip" v-text="item.tip"></p>
                                <div>
                                    <a href="javascript:void(0)" v-text="item.title"></a>
                                    <p><span class="one-re-course-price">￥{{item.price}}</span> · {{item.level}} · <span class="one-re-course-count">{{item.count}}</span></p>
                                </div>
                            </li>
                        </ul>
                    </div>
                    <div class="right-content-1">
                        <p class="add-title-1">热门专题标签</p>
                        <a class="hot-tip hot-tip-1" href="javascript:void(0)">PHP主流框架</a>
                        <a class="hot-tip hot-tip-2" href="javascript:void(0)">数据科学</a>
                        <a class="hot-tip hot-tip-3" href="javascript:void(0)">Thinkphp实例教程</a>
                        <a class="hot-tip hot-tip-4" href="javascript:void(0)">Yii框架实战项目</a>
                    </div>
                    <div class="right-content-1">
                        <p class="add-title-1">相关课程</p>
                        <ul>
                            <li class="one-re-course" v-for="(item, index) in reCourse" v-bind:key="index">
                                <img v-bind:src="item.img">
                                <p class="one-re-course-tip" v-text="item.tip"></p>
                                <div>
                                    <a href="javascript:void(0)" v-text="item.title"></a>
                                    <p><span class="one-re-course-price">￥{{item.price}}</span> · {{item.level}} · <span class="one-re-course-count">{{item.count}}</span></p>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>
                <div style="clear: both"></div>
            </div>
        </div>
    </div>
</template>

<script>
import '../../static/css/detail.css';
import reCourse from '../../static/json/reCourse.json';

export default {
    data() {
        return {
            reCourse,
            course: {}
        }
    },
    created : function() {
        import('../../static/json/course' + this.$route.params.id + '.json').then(res => {
            this.course = res;
        });
    },
    mounted() {
        document.getElementById("nav").classList.add("nav-1");
        document.getElementById("footer").classList.add("footer-1");
        
        let searchTag = document.getElementsByClassName("search-tag");

        for (let i = 0; i < searchTag.length; i++) {
            searchTag[i].classList.add("search-tag-1");
        }

        this.$emit('logoSrc', '../../static/img/logo-1.png');
    }
}
</script>

