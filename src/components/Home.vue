<template>
    <div class="container">
        <div class="banner-container">
            <div class="banner-box">
                <div class="menuwrap"></div>
                <div v-for="(sub,i) in menu" class="submenu"  style="display: none;"  v-bind:key="i"  @mouseover="menuOver($event,i)" @mouseout="menuOut($event,i)">
                    <div class="innerBox clearfix">
                        <div class="subinnerBox">
                            <div class="cates-box">
                                <div class="fe-base-box clearfix">
                                    <div class="banner-line">
                                        <span class="bold mr10 l small-title">{{sub.tech.title}}</span>
                                    </div>
                                    <div class="tag-box l">                    
                                        <a v-for="(classify,idx) in sub.tech.classify" target="_blank" href="javascript:void(0)"  v-bind:key="idx">{{classify}}</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="recomment-box" >
                        <div v-for="(recommend,idxs) in sub.tech.recommend"  class="l banner-course-card" v-bind:key="idxs">
			                <a href="javascript:void(0)" target="_blank" v-bind:title="recommend.name" class="clearfix">
			                    <img v-bind:src="recommend.src" class="l">
			                    <div class="l course-card" style="padding: 0;">
			                        <h3 class="course-card-name">{{recommend.name}}</h3>	
							        <div class="course-card-price l">￥{{recommend.price}}.00</div>
									<div class="course-card-dot l"><i class="imv2-dot_samll">&nbsp;&nbsp;·&nbsp;&nbsp;</i></div>
						            <div class="course-card-info l">{{recommend.level}}</div>
						            <div class="course-card-dot l"><i class="imv2-dot_samll">&nbsp;&nbsp;·&nbsp;&nbsp;</i></div>
						            <div class="course-card-info l"><i class="icon-set_sns"></i>{{recommend.count}}</div>
			                    </div>
			                </a>
		                </div>
	                </div>
                </div>
                <div class="menu-wrap menu-content">
                    <div v-for="(item,index) in menu" v-bind:class="classArray[index]" @mouseover="menuOver($event,index)" @mouseout="menuOut($event,index)" v-bind:key="index">
                        <a href="javascript:void(0)">{{item.name}}</a>
                    </div>
                </div>
                <div class="banner-content">
                    <div class="banner">
                        <img v-bind:src="item" v-for="(item, index) in banner" v-bind:style="imgLs[index]" v-bind:key="index"  class="banner-img">
                        <ul class="banner-dots">
                            <li class="banner-dot" v-bind:class="item.display == 'block' && item.opacity == 1 ? 'banner-dot-sl' : ''" v-on:mouseover="imgMouseOver" v-on:mouseout="imgMouseOut" v-on:click="imgChange(imgNow, index)" v-for="(item, index) in imgLs" v-bind:key="index" ></li>
                        </ul>
                        <a v-on:mouseover="imgMouseOver" v-on:mouseout="imgMouseOut" v-on:click="imgChange(imgNow, imgNow - 1)" class="banner-btn banner-btn-left">&lt;</a>
                        <a v-on:mouseover="imgMouseOver" v-on:mouseout="imgMouseOut" v-on:click="imgChange(imgNow, imgNow + 1)" class="banner-btn banner-btn-right">&gt;</a>
                    </div>
                    <ul class="banner-path">
                        <li class="banner-path-li">
                            <i></i>
                            <p class="tit">Web前端攻城狮</p>
                            <p class="desc">互联网时代最火爆的技术</p>
                        </li>
                        <li class="banner-path-li">
                            <i></i>
                            <p class="tit">Java攻城狮</p>
                            <p class="desc">综合就业排名第一</p>
                        </li>
                        <li class="banner-path-li">
                            <i></i>
                            <p class="tit">Android攻城狮</p>
                            <p class="desc">移动设备市场份额第一</p>
                        </li>
                        <li class="banner-path-li">
                            <i></i>
                            <p class="tit">PHP攻城狮</p>
                            <p class="desc">世界上最好的语言：）</p>
                        </li>
                        <li class="banner-path-li">
                            <i></i>
                            <p class="tit">iOS攻城狮</p>
                            <p class="desc">可能是全球最好用的系统</p>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
        <!-- 实战推荐 -->
        <div class="recommend-container">
            <div class="recommend-box">
                <h3 class="recommend-title">
                    <span class="span-left"></span>
                    <em>实</em> /
                    <em>战</em> /
                    <em>推</em> /
                    <em>荐</em>
                    <span class="span-right"></span>
                </h3>
                <div class="recommend-content">
                    <div v-on:click="goToDetail(item.id)" class="course-box" v-for="(item, index) in recommend" v-bind:key="index">
                        <img v-bind:src="item.courseBanner" class="course-banner">
                        <div class="course-card">
                            <h3 class="course-name" v-text="item.courseName"></h3>
                            <div class="course-info">
                                <span v-text="item.courseLevel"></span>
                                <span>
                                    <i class="icon-count"></i>
                                    <span v-text="item.count">2018</span>
                                </span>
                            </div>
                            <div class="course-price" v-text="item.coursePrice">
                            </div>
                        </div>
                        <div class="course-tip">
                            <a href="javascript:void(0)" v-for="(tipItem, tipIndex) in item.courseTips" v-bind:key="tipIndex" v-text="tipItem"></a>
                        </div>
                    </div>
                </div>
            </div>            
        </div>
        <!-- 新上好课 -->
        <div class="fresh-container">
            <div class="fresh-box">
                <h3 class="fresh-title">
                    <span class="span-left"></span>
                    <em>新</em> /
                    <em>上</em> /
                    <em>好</em> /
                    <em>课</em>
                    <span class="span-right"></span>
                </h3>
                <div class="fresh-content">
                    <div v-on:click="goToDetail(item.id)" class="course-box" v-for="(item, index) in fresh" v-bind:key="index">
                        <img v-bind:src="item.courseBanner" class="course-banner">
                        <div class="course-card">
                            <h3 class="course-name" v-text="item.courseName"></h3>
                            <div class="course-info">
                                <span v-text="item.courseLevel"></span>
                                <span>
                                    <i class="icon-count"></i>
                                    <span v-text="item.count">2018</span>
                                </span>
                            </div>
                            <div class="course-price" v-text="item.coursePrice">
                            </div>
                        </div>
                        <div class="course-tip">
                            <a href="javascript:void(0)" v-for="(tipItem, tipIndex) in item.courseTips" v-bind:key="tipIndex" v-text="tipItem"></a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- 新手入门 -->
        <div class="noob-container">
            <div class="noob-box">
                <h3 class="noob-title">
                    <span class="span-left"></span>
                    <em>新</em> /
                    <em>手</em> /
                    <em>入</em> /
                    <em>门</em>
                    <span class="span-right"></span>
                </h3>
                <div class="noob-content">    
                    <div class="noob-add">
                        <a href="javascript:void(0)">
                            <h3 class="add-title">Web前端入门到精通，最全学习路线</h3>
                            <p class="add-desc">零基础入门Web前端开发的必备课程</p>
                        </a>
                        <a href="javascript:void(0)">
                            <h3 class="add-title">求职旺季，如何避开面试官套路？</h3>
                            <p class="add-desc">技能+技巧，心水Offer尽收囊中！</p>
                        </a>
                    </div>
                    <div v-on:click="goToDetail(item.id)" class="course-box" v-for="(item, index) in noob" v-bind:key="index">
                        <img v-bind:src="item.courseBanner" class="course-banner">
                        <div class="course-card">
                            <h3 class="course-name" v-text="item.courseName"></h3>
                            <div class="course-info">
                                <span v-text="item.courseLevel"></span>
                                <span>
                                    <i class="icon-count"></i>
                                    <span v-text="item.count">2018</span>
                                </span>
                            </div>
                            <div class="course-price" v-text="item.coursePrice">
                            </div>
                        </div>
                        <div class="course-tip">
                            <a href="javascript:void(0)" v-for="(tipItem, tipIndex) in item.courseTips" v-bind:key="tipIndex" v-text="tipItem"></a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- 技能提升 -->
        <div class="promote-container">
            <div class="promote-box">
                <h3 class="promote-title">
                    <span class="span-left"></span>
                    <em>技</em> /
                    <em>能</em> /
                    <em>提</em> /
                    <em>升</em>
                    <span class="span-right"></span>
                </h3>
                <div class="promote-content">    
                    <div class="promote-add">
                        <a href="javascript:void(0)">
                            <h3 class="add-title">用最短的时间高效地学习Python全指导</h3>
                            <p class="add-desc">从菜鸟到phthoner，最新最全的学习路线，让你更专业！</p>
                        </a>
                        <a href="javascript:void(0)">
                            <h3 class="add-title">进入React JS世界，从入门到实战无障碍升级</h3>
                            <p class="add-desc">贯穿案例与项目实战，快速上手企业开发</p>
                        </a>
                    </div>
                    <div v-on:click="goToDetail(item.id)" class="course-box" v-for="(item, index) in promote" v-bind:key="index">
                        <img v-bind:src="item.courseBanner" class="course-banner">
                        <div class="course-card">
                            <h3 class="course-name" v-text="item.courseName"></h3>
                            <div class="course-info">
                                <span v-text="item.courseLevel"></span>
                                <span>
                                    <i class="icon-count"></i>
                                    <span v-text="item.count">2018</span>
                                </span>
                            </div>
                            <div class="course-price" v-text="item.coursePrice">
                            </div>
                        </div>
                        <div class="course-tip">
                            <a href="javascript:void(0)" v-for="(tipItem, tipIndex) in item.courseTips" v-bind:key="tipIndex" v-text="tipItem"></a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- 前沿技术 -->
        <div class="front-container">
            <div class="front-box">
                <h3 class="front-title">
                    <span class="span-left"></span>
                    <em>前</em> /
                    <em>沿</em> /
                    <em>技</em> /
                    <em>术</em>
                    <span class="span-right"></span>
                </h3>
                <div class="front-content">    
                    <div class="front-add">
                        <a href="javascript:void(0)">
                            <h3 class="add-title">算法内外功兼修训练营</h3>
                            <p class="add-desc">面试基础储备与项目开发中的算法应用，玩转算法、高效开发！</p>
                        </a>
                        <a href="javascript:void(0)">
                            <h3 class="add-title">打开Spring Boot学习的最佳方式</h3>
                            <p class="add-desc">直击Spring Boot框架核心，颠覆Java企业应用开发</p>
                        </a>
                    </div>
                    <div v-on:click="goToDetail(item.id)" class="course-box" v-for="(item, index) in front" v-bind:key="index">
                        <img v-bind:src="item.courseBanner" class="course-banner">
                        <div class="course-card">
                            <h3 class="course-name" v-text="item.courseName"></h3>
                            <div class="course-info">
                                <span v-text="item.courseLevel"></span>
                                <span>
                                    <i class="icon-count"></i>
                                    <span v-text="item.count">2018</span>
                                </span>
                            </div>
                            <div class="course-price" v-text="item.coursePrice">
                            </div>
                        </div>
                        <div class="course-tip">
                            <a href="javascript:void(0)" v-for="(tipItem, tipIndex) in item.courseTips" v-bind:key="tipIndex" v-text="tipItem"></a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- 精彩手记及猿问 -->
        <div class="note-container">
            <div class="note-box">
                <h3 class="note-title">
                    <span class="span-left"></span>
                    <em>精</em> /
                    <em>彩</em> /
                    <em>手</em> /
                    <em>记</em> /
                    <em>及</em> /
                    <em>猿</em> /
                    <em>问</em>
                    <span class="span-right"></span>
                </h3>
                <div class="note-content">
                    <div class="note" v-for="(item, index) in note" v-bind:key="index">
                        <p class="note-label"> {{item.noteLabel}}</p>
                        <p class="note-question" v-text="item.noteQuestion"></p>
                        <p class="note-answer">共{{item.answerNum}}个回答 -></p>
                    </div>
                </div>
            </div>
        </div>
        <!-- 慕课精英名师 -->
        <div class="teacher-container">
            <div class="teacher-box">
                <h3 class="teacher-title">
                    <span class="span-left"></span>
                    <em>慕</em> /
                    <em>课</em> /
                    <em>精</em> /
                    <em>英</em> /
                    <em>名</em> /
                    <em>师</em>
                    <span class="span-right"></span>
                </h3>
                <div class="teacher-content">
                    <div class="teacher-broadcast-out">
                        <ul class="teacher-broadcast-in">
                            <li class="one-teacher" v-for="(item, index) in teacher" v-bind:key="index">
                                <div class="teacher-card">
                                    <h3 class="teacher-name" v-text="item.teacherName"></h3>
                                    <h4 class="teacher-desc" v-text="item.teacherDsec"></h4>
                                    <p class="teacher-detail" v-text="item.teacherDeatail"></p>
                                </div>
                                <img v-bind:src="item.teacherHead" class="teacher-head">
                            </li>                  
                        </ul>
                    </div>
                </div>
            </div>
        </div>
        <!-- 吊炸天全明星 -->
        <div class="star-container">
            <div class="star-box">
                <h3 class="star-title">
                    <span class="span-left"></span>
                    <em>吊</em> /
                    <em>炸</em> /
                    <em>天</em> /
                    <em>全</em> /
                    <em>明</em> /
                    <em>星</em>
                    <span class="span-right"></span>
                </h3>
                <div class="star-content">
                    <ul class="big-stars">
                        <li class="big-star" v-for="(item, index) in bigStar" v-bind:key="index">
                            <div v-bind:class="['champion', 'champion-' + item.level]"></div>
                            <img v-bind:src="item.head" class="big-star-head">
                            <p class="big-star-name" v-text="item.name"></p>
                            <p class="big-star-desc" v-text="item.desc"></p>
                        </li>
                    </ul>
                    <div class="small-stars">
                        <ul>
                            <li class="small-star" v-for="(item, index) in smallStar1" v-bind:key="index"><a href="javscript:void(0)">
                                <img v-bind:src="item.img"></a></li>
                        </ul>
                        <ul>
                            <li class="small-star" v-for="(item, index) in smallStar2" v-bind:key="index"><a href="javscript:void(0)">
                                <img v-bind:src="item.img"></a></li>
                        </ul>
                    </div>
                </div>
            </div>            
        </div>
    </div>
</template>

<script>
import '../../static/css/home.css';
import recommend from '../../static/json/recommend';
import fresh from '../../static/json/fresh';
import noob from '../../static/json/noob';
import promote from '../../static/json/promote';
import front from '../../static/json/front';
import note from '../../static/json/note';
import teacher from '../../static/json/teacher';
import bigStar from '../../static/json/bigStar.json';
import smallStar1 from '../../static/json/smallStar1.json';
import smallStar2 from '../../static/json/smallStar2.json';
import banner from '../../static/json/banner.json';
import menu from '../../static/json/menu.json';

export default {
    data() {
        return {
            recommend,
            fresh,
            noob,
            promote,
            front,
            note,
            teacher,
            bigStar,
            smallStar1,
            smallStar2,
            banner,
            menu,
            imgLs: [],
            imgNow: 0,
            itv: undefined,
            itvAll: undefined,
            classArray: []
        }
    },
    methods: {
        goToDetail(id) {
            this.$router.push('/detail/' + id +'/');
        },
        imgChange(from, to) {
            if (to >= this.imgLs.length) {
                to = 0;
            } else if (to < 0) {
                to = this.imgLs.length - 1;
            }

            this.imgLs[to].display = 'block';

            let op = 1;

            clearInterval(this.itv);

            this.itv = setInterval(function() {
                op -= 0.05;

                this.imgLs[from].opacity = op;

                if (op <= 0) {
                    clearInterval(this.itv);

                    this.imgLs[from].display = 'none';
                    this.imgLs[from].opacity = 1;
                    this.imgLs[from].zIndex = 0;
                    this.imgLs[to].zIndex = 1;
                    this.imgNow = to;
                }
            }.bind(this), 15);
        },
        imgMouseOver() {
            clearInterval(this.itvAll);

        },
        imgMouseOut() {
            this.itvAll = setInterval(function() {
                if (this.imgNow == this.imgLs.length - 1) {
                    this.imgChange(this.imgNow, 0);
                } else {
                    this.imgChange(this.imgNow, this.imgNow + 1);
                }
            }.bind(this), 1000);
        },        
        menuOver($event,index) {
            this.classArray[index].push("menu-item-on");
            document.getElementsByClassName("submenu")[index].style.display="block";
        },
        menuOut($event,index) {
            this.classArray[index].pop("menu-item-on");
            document.getElementsByClassName("submenu")[index].style.display="none";
        }
    },
    mounted() {
        document.getElementById("nav").classList.remove("nav-1");
        document.getElementById("footer").classList.remove("footer-1");
        
        let searchTag = document.getElementsByClassName("search-tag");

        for (let i = 0; i < searchTag.length; i++) {
            searchTag[i].classList.remove("search-tag-1");
        }

        this.$emit('logoSrc', '../../static/img/logo.png');

        this.banner.forEach(() => {
            this.imgLs.push({
                display: 'none',
                opacity: 1,
                zIndex: 0
            });
        });

        this.imgLs[0].display = 'block';
        this.imgLs[0].zIndex = 1;

        this.itvAll = setInterval(function() {
            this.imgChange(this.imgNow, this.imgNow + 1);
        }.bind(this), 2000);
        
        for (let i = 0; i < menu.length; i++) {
            this.classArray.push(["item"]);
        }
    }
}
</script>

