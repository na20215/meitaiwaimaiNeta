<template>
    <div class="mainPart3">
      <div class="part3Title" ref="header">
        <img src="https://s3plus.meituan.net/v1/mss_4067b040e3364072a20737a5254654ea/waimai-cfe-custom-pc-08ddc77d/production/assets/story-7c3e0597d5.png">
      </div>
      <div class="maintainPart" ref="main">
        <div class="previousPage" @click="previousPage"><span>&lt;</span></div>
        <div class="slipWindow">
          <div class="outer">
          <div class="film" ref="film">
            <div 
            v-for="(story, idx) in stories"
             :key="idx"
             class="stories"
             @mouseover="stopCarousel()" 
            @mouseleave="restartCarousel()"
              >
              <div class="content">
                <div class="titlePart">
                  <img class="logo" src="https://p0.meituan.net/travelcube/22d5fe01d4eb54ce117cc96377fe9c1d4418.png">
                  <div>{{ story.name }}</div>
                </div>
                <h2 class="title">{{ story.Title }}</h2>
                <div class="detail">{{ story.storyContent }}</div>
                <div class="button">查看详情 </div>
              </div>
              <img :src="story.storyPath">
            </div>
          </div>
        </div>
        </div>
        <div class="nextPage" @click="nextPage"><span>></span></div>
      </div>
      <div class="guideButton">
          <div
          v-for="(circle,idx) in group"
          :key="idx" 
          class="circle"
          :class="{active: numPage === idx}"
          @click="setTheStory(idx)"
          @mouseover="stopCarousel()" 
          @mouseleave="restartCarousel()">
        </div>

      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        numPage: 0,
        stories: [
          {
            name:'美团服务市场',
            storyPath:'https://p0.meituan.net/travelcube/609cd1a366066c8eff61b20c551bcb6074788.jpg',
            Title:'米粉面馆接入经营助手服务，收入增幅达51.52%',
            storyContent:'开一家店有多操心？加盟、选址、经营、管理到真正赚钱，期间的辛苦只有每家店老板才深有体会。美团服务市场聚集垂直领域优质服务商，打造一站式服务生态！从新店开业到老店升级、从店铺装修到营销托管、从食材供应到金融服务等，为所有商家提供店铺经营全方位服务，解决经营所遇难题，助力轻松做生意。',
            href:'https://waimai.meituan.com/cpc/csrpc/story.html?page_name=one',
          },{
            name:'美团外卖骑手人物：李军',
            storyPath:'https://p0.meituan.net/travelcube/39003b966800f685d2b82c73e5fa8b2d96534.jpg',
            Title:'为减肥而成为美团兼职骑手，后来副业变“主业”',
            storyContent:'李君是11位骑手中的一位，来自内蒙古包头市，他近三个月的准时率平均达到了99.9%，满意度100。当问到他知道自己可以去俄罗斯看世界杯时是什么心情，李君说接到电话刚开始不敢相信，后来反应过来就直接飞奔回家拿上身份证就去办加急护照了。开心激动的心情久久难平复……',
            href:'https://waimai.meituan.com/cpc/csrpc/story.html?page_name=two',
          },{
            name:'美团外卖骑手人物：徐振',
            storyPath:'https://p0.meituan.net/travelcube/583387bb07e6701874c71aeddc051b7590731.jpg',
            Title:'平凡之路上的英雄梦',
            storyContent:'我觉得自从成了美团众包骑手之后，遇到了很多有趣新奇的人和事。以前我的生活比较单调，上班、回家两点一线。加入美团众包后，认识了许多朋友，帮助了一些人也得到了一些人的帮助。美团众包，为我的生活打开了一扇新的大门。我喜欢它的弹性、自由，让我对生活有了更多的掌控......',
            href:'https://waimai.meituan.com/cpc/csrpc/story.html?page_name=three ',
          }
        ],
        group:['first','second','third'],
        isLocked: false,
      };
    },
    methods: {
      nextPage() {
        this.numPage++;
        if (this.numPage === this.stories.length ) {
            this.stories.push(this.stories[0]);
            this.scrollPage();
            this.numPage = 0;
            setTimeout(() => {
            const film = this.$refs.film;
            film.style.transition = "none";
            film.style.transform = `translateX(0%)`;
            this.scrollPage();
            this.stories.pop();
            film.style.transition = "transform 0.5s ease";
            }, 500);
          return;
        }
        this.scrollPage();
      },
      previousPage() {
        if (this.isLocked) return;
        this.numPage--;
         if (this.numPage < 0) {
             this.isLocked = true; //有bug，先规避；
             requestAnimationFrame(()=>{
             this.$refs.film.style.transition = "none";
             this.numPage = 0;
             this.stories.unshift(this.stories[this.stories.length-1]);
             this.$refs.film.style.transform = `translateX(-100%)`;
             this.scrollPage();
             });
             setTimeout(() => {
                this.$refs.film.style.transition = "none";
                this.$refs.film.style.transform = `translateX(-300%)`;
                this.stories.shift();
                this.$refs.film.style.transition = "none";
                this.$refs.film.style.transform = `translateX(-200%)`;
                this.numPage = this.stories.length -1 ;
                this.isLocked = false;
            },500)
             
        }
         this.scrollPage();
      },
      scrollPage() {
        const offset = -this.numPage * this.$refs.film.clientWidth;
        this.$refs.film.style.transform = `translateX(${offset}px)`;
        this.$refs.film.style.transition = "all 0.5s ease";
      },
      setTheStory(idx){
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
    mounted() {
        this.startCarousel()

    },
    beforeUnmount() {
        this.stopCarousel()

    },
  };
  </script>
  
  <style scoped>
  .mainPart3 {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: rgb(255,207,91);
    height: 55rem;
    gap: 4rem;
  }
  .part3Title {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 5rem;
    opacity: 0;
    transform: translateY(4rem);
    transition: 0.5s;
  }
  .part3Title.enter {
    opacity: 1;
    transform: translateY(0);
  }

  .part3Title > img {
    width: 20rem;
    height: 8rem;
  }
  .maintainPart {
    display: flex;
    height: 26.5rem;
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
  .previousPage, .nextPage {
    z-index: 3;
    display: flex;
    width: 8%;
    justify-content: center;
    align-items: center;
    font-size: 2rem;
    cursor: pointer;
  }
  .previousPage > span:hover, .nextPage > span:hover {
    color: white;
  }
  .slipWindow {
    position: relative;
    display: flex;
    align-items: center;
    flex: 10;
    width: 84%;
    overflow: hidden;

  }
  .slipWindow::before {
    position: absolute;
    z-index: 0;
    content: '';
    height: 100%;
    width: 80%;
    right: 0;
    border-radius: 1rem;
    background: linear-gradient(to right, rgb(255, 119, 74), rgb(255, 155, 74));
  }
  .outer{
    position: absolute;
    display: flex;
    align-items: center;
    flex: 10;
    width: 95%;
    overflow: hidden;
    height: 100%;
  }
  .film {
    z-index: 1;
    display: flex;
    flex-direction: row;
    height: 80%;
    width: 100%;

  }
   .film > .stories{
    z-index: 2;
    flex: 0 0 100%; 
    opacity: 1;
    height: 100%;
    display: flex;
    flex-direction: row;
    cursor: pointer;
    position: relative;
  }

  .stories > .content {
    display: flex;
    flex-direction: column;
    width: auto;
    height: 100%;
    background-color: white;
    box-sizing: border-box;
    padding: 2rem;
    gap: 0.85rem;
  } 
  .stories > .content > .titlePart{
    display: flex;
    flex-direction: row;
    align-items: center;
    box-sizing: border-box;
    gap:0.5rem;
  }
  .stories > img {
    z-index: 5;
    height: 100%;
    width: auto;
  } 
 
 img.logo {
    height:  auto;
    width: 2rem;
  }

  .guideButton{
    display: flex;
    flex-direction: row;
    transform: translateY(-2rem);
  }

.circle {
  width: 0.8rem;
  height: 0.8rem;
  border-radius: 50%;
  background-color: white;
  display: inline-block;
  margin: 0.5rem;
}
.circle:hover {
  background-color: rgb(255,92,73);
}
.circle.active {
  background-color:  rgb(255,92,73);
}
h2.title{
  margin: 0;
  padding:0;
  font-size: 1.375rem;
}
.detail{
  color: gray;
  line-height: 175%;
}
.button{
  position: absolute;
  border: 0.11rem solid rgb(255,207,91);
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
  </style>
  