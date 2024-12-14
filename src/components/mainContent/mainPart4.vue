<template>
    <div class="mainPart4">
        <div class="part4Title" ref="header">
        <img src="../../assets/23.png">
      </div>
      <div class="maintainPart" ref="main">
            <div class="slidingWindow">
                <div class="outer">
                    <div class="shell"><div class="film" ref="film">
                        <div 
                        v-for="(New,idx) in News"
                        :key="idx"
                        class="New">
                        <img class="news" :src="New.img">
                        <h2 class="newsTitle text-container">{{ New.Title }}</h2>
                        <div class="newsContent">{{ New.Content }}</div>
                        <div class="button">查看详情</div>
                    </div>
                </div></div>
                    <div class="switchButton">
                        <div class="idx">0{{ numPage + 1  }}</div>
                        <div 
                        v-for="(btn,idx) in buttonBox"
                        :key="idx"
                        class="circleButton"
                        :class="{active: numPage===idx}"
                        @click="setThePage(idx)"></div>
                    </div>
                </div>
            </div>
            <div class="textNews">
                <h1>2018年度媒体报道</h1>
                <ul class="newList">
                    <li 
                    v-for="(New,idx) in News"
                    :key="idx"
                    >0{{idx + 1}} {{ New.TitleText }}</li>

                </ul>
            </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
        data() {
            return {
                numPage: 0,
                buttonBox:['01','02','03','04','05','06'],
                News:[
                    {
                    Title:'保障骑手安心无忧送餐路 美团外卖首发《骑手生活安全指',
                    TitleText:'保障骑手安心无忧送餐路 美团外卖首发《骑手生活安全指南》',
                    Content:'随着大众餐饮消费升级，外卖行业发展迅速。数据显示，2017年美团外卖日完成订单量突破2100万单，稳居行业第一，成...',
                    img:require('../../assets/24.jpg'),

                    },
                    {
                    Title:'MINISO名创优品正式入驻美团闪购 时尚单品30分钟送达',
                    TitleText:'MINISO名创优品正式入驻美团闪购 时尚单品30分钟送达',
                    Content:'美团闪购与设计师品牌MINISO名创优品共同发布消息，双方即日起正式开展品牌合作，名创优品在北京、上海、广州、深...',
                    img:require('../../assets/25.jpg'),

                    },
                    {
                    Title:'专业食品安全检测团队进驻美团点评 从此舌尖安全有他们',
                    TitleText:'专业食品安全检测团队进驻美团点评 从此舌尖安全有他们守护',
                    Content:'外卖订餐平台对合作商户的食品安全监察力度再次加码。近日,美团点评先后与检科测试集团有限公司、中农孚德检测技术...',
                    img:require('../../assets/26.jpg'),

                    },
                    {
                    Title:'Trustdata发布2018上半年外卖份额数据 美团饿了么百度',
                    TitleText:'Trustdata发布2018上半年外卖份额数据 美团饿了么百度“631”格局三分天下',
                    Content:'报告显示，美团外卖以59%的市场交易额领跑行业，相当于饿了么与百度外卖市场交易额之和的1.5倍，互联网外卖行业呈...',
                    img:require('../../assets/27.jpg'),
                        
                    },
                    {
                    Title:'美团上线闪购业务 以“快”破局助力零售升级',
                    TitleText:'美团上线闪购业务 以“快”破局助力零售升级',
                    Content:'7月18日，美团点评举办“以快破局•助力零售升级” 2018美团闪购发布会，正式上线美团闪购业务，涵盖超市便利、生鲜果...',
                    img:require('../../assets/28.jpg'),
                        
                    },
                    {
                    Title:'美团城市新青年 外卖骑手正能量图鉴',
                    TitleText:'美团城市新青年 外卖骑手正能量图鉴',
                    Content:'一个时代的性格，是青年代表的性格；一个时代的精神，是青年代表的精神。美团外卖骑手群体正是一群努力学习提升自...',
                    img:require('../../assets/29.jpg'),
                    },

                ]
            }

        },
        mounted(){
            this.startCarousel();
        },
        beforeUnmount(){
            this.stopCarousel();
        },
        methods: {
            nextPage() {
                this.numPage++;
                if(this.numPage >= this.News.length ){
                    this.numPage = 0 ;
                }
                this.scrollPage();
            },
            scrollPage(){
                const offset = -this.numPage * this.$refs.film.clientHeight;
                this.$refs.film.style.transform = `translateY(${offset}px)`;
                this.$refs.film.style.transition = "all 0.5s ease";
            },
            setThePage(idx){
                this.numPage = idx;
                this.scrollPage();
            },
            startCarousel(){
                this.carouselInterval = setInterval(this.nextPage, 5000);
            },
            restartCarousel(){
                this.startCarousel();
            },
            stopCarousel() {
                clearInterval(this.carouselInterval); 
            },
        },
  }
  </script>
  
  <style scoped>
    .mainPart4{
        width: 100%;
        background-color: white;
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 55rem;
        gap: 4rem;
    }

    .part4Title {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 5rem;
        opacity: 0;
        transform: translateY(4rem);
        transition: 0.5s;
    }

    .part4Title.enter {
        opacity: 1;
        transform: translateY(0);
    }

    .part4Title > img {
        width: 20rem;
        height: 8rem;
    }

    .maintainPart {
        display: flex;
        flex-direction: row;
        height: 35rem;
        width: 60%;
        overflow: hidden;
        opacity: 0;
        transform: translateY(4rem);
        transition: 0.5s;
    }

    .maintainPart.enter {
        opacity: 1;
        transform: translateY(0);
    }

    .maintainPart > .slidingWindow{
        width: 50%;
        height:100%;
        display: flex;
        justify-content: center;
    
    }
    .maintainPart > .slidingWindow > .outer{
        position: relative;
        width: 62.5%;
        height: 90%;
        border-radius: 0.25rem;
        box-shadow: 0 0 0.1rem 0.1rem rgb(240,240, 240); 
    }
    .maintainPart > .slidingWindow > .outer::after{
        z-index: -1;
        position: absolute;
        right: -2rem;
        bottom: -1.5rem;
        content: '';
        background-color: rgb(255,207,91);
        width: 100%;
        height: 100%;
        border-radius: 0.25rem;
    }
    .maintainPart > .slidingWindow > .outer > .switchButton{
        position: absolute;
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 1.5rem;
        height: auto;
        right: -1.75rem;
        bottom: 2rem;
        background-color: rgb(255,207,91);
        border-radius: 0;
        gap: 0.1rem;   
    }
    .idx{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
    }
    .circleButton{
        width: 0.4rem;
        height: 0.4rem;
        border: 0.05rem solid rgb(55,54,51);
        border-radius: 50%;
        background-color: rgb(255,207,91);
        display: inline-block;
        margin: 0.1rem;
    }
    .circleButton:hover{
        background-color: rgb(55,54,51) ;
    }
    .circleButton.active{
        background-color: rgb(55,54,51) ;
    }
    .maintainPart > .slidingWindow > .outer > .shell{
        width: 100%;
        height: 100%;
        overflow: hidden;
        border-radius: 0.25rem;
    
    }
    .maintainPart > .slidingWindow > .outer > .shell > .film{
        display: flex;
        flex-direction: column;
        width: 100%;
        height: 100%;  
        border-radius: 0.25rem;
    }
    .New{
        flex: 0 0 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        box-sizing: border-box;
        background-color: white;
        position: relative;
    }
    img.news{
        width:100%;
    }
    .New > .newsTitle{
        box-sizing: border-box;
        padding: 0rem 1rem;
        position: relative;
    }

    .New > .newsContent{
        display: flex;
        flex-direction: row;
        box-sizing: border-box;
        padding: 1.75rem;
        color: rgb(141,141,141);
        font-size: 1rem;
        line-height: 175%;
    }
    .New > .newsTitle::after{
        position:absolute;
        bottom:-1rem;
        left: 0;
        content: '';
        background-color: rgb(61,61,61);
        width: 4rem;
        height: 0.3rem;
        margin: 0rem 1rem;
    }
    .button{
        position: absolute;
        border: 0.12rem solid rgb(255,207,91);
        width: 5rem;
        height: 1.8rem;
        border-radius: 0.9rem;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        bottom: 2rem;
        left: 2rem;
        color: rgb(255,207,91);
    }

    .button:hover{
        background-color: rgb(255,207,91);
        color: white;
    }


  .maintainPart > .textNews{
    width: 50%;
    height:100%;
  }

  .newList{
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    gap: 2rem;
    width: 100%;
  }

  li {
    overflow: hidden;   
    text-overflow: ellipsis;
    width: 32rem;
    white-space: nowrap; 
    transition: all 0.5s ease,
  }

  li:hover {
    font-size: 1.2rem;
    font-weight: bolder;
  }
 
  </style>