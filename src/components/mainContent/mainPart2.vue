<template>
  <div class="mainPart2">
    <div class="TitleIntroduction" ref="header">
        <img class="ServiceTitle" src="https://s3plus.meituan.net/v1/mss_4067b040e3364072a20737a5254654ea/waimai-cfe-custom-pc-08ddc77d/production/assets/serviceintro-cb423af0c3.png">
    </div>
    <div class="showPart" ref="title">
        <div class="SelectPart">
            <h1 class="head" >品类全覆盖，应有尽有</h1>
            <div 
                v-for="(selection,idx) in catergorySelection"
                :key="idx"
                class="catergory"
                :class="{selectionActive: ActivePage === idx, }"
                @mouseover="setActivePage(idx)" 
                @mouseleave="restartCarousel()">
                <div class="iconframe">
                    <img class="unSelected" 
                        :class="{active: ActivePage === idx}"
                        :src="selection.iconPath">
                    <img class="selected" 
                        :class="{active: ActivePage === idx}"
                        :src="selection.iconPathActive">
                </div>
                <div class="textFrame">
                    <div class="mainText" :class="{active: ActivePage === idx}">{{ selection.name }}</div>
                    <div class="subText" :class="{active: ActivePage === idx}">{{ selection.subTitle }}</div>
                </div>
            </div>
        </div>
        <div class="viewPart" ref="viewAnime">
            <img class="phoneEdge" src="https://s3plus.sankuai.com/v1/mss_c4375b35f5cb4e678b5b55a48c40cf9d/waimai-c-iweb/%E6%89%8B%E6%9C%BA%E5%A4%96%E5%A3%B32%402x.png">
            <img 
              v-for="(page, idx) in AppPage"
              :key="idx"
              :src="page"
              class="phonePage"
              :class="{ active: ActivePage === idx }"
            >

        </div>
    </div>
  </div>
</template>

<script>

export default {
    data() {
        return {
            ActivePage: 0,
            totalPages: 4,
            catergorySelection:[
                {
                    name:'美食 Delicacy',
                    subTitle:'大牌优惠',
                    iconPath:'https://p0.meituan.net/travelcube/88404bd7e01d3e750712ab5fa32237f51546.png',
                    iconPathActive:'https://p1.meituan.net/travelcube/d021ba06885ae9377e555a76a6a27f762776.png',
                },
                {
                    name:'甜品饮品 Desserts&Drinks',
                    subTitle:'幸福甜蜜',
                    iconPath:'https://p0.meituan.net/travelcube/d6840d5c3f8a35db3c643bb70bdf1b0a2176.png',
                    iconPathActive:'https://p1.meituan.net/travelcube/031c712bdf99b4e11c7c286af7c8d6593495.png',
                },
                {
                    name:'水果生鲜 Fresh foods',
                    subTitle:'新鲜速达',
                    iconPath:'https://p1.meituan.net/travelcube/de0c9acd3d5711e482b9c029d1ee46702136.png',
                    iconPathActive:'https://p0.meituan.net/travelcube/6a035852652f87c108934a64409817d73462.png',
                },
                {
                    name:'超市便利 SuperMarket',
                    subTitle:'优惠促销',
                    iconPath:'https://p0.meituan.net/travelcube/88404bd7e01d3e750712ab5fa32237f51546.png',
                    iconPathActive:'https://p0.meituan.net/travelcube/92a1e16f420880cbc6bac9a6054530b82289.png',
                }
            ],
            AppPage:[
                'https://p0.meituan.net/travelcube/39255a16d132c9c806ee59707b8bff5d705260.png',
                'https://p0.meituan.net/travelcube/4ac7153d262dda2248aaf9500f0626d8422358.png',
                'https://p0.meituan.net/travelcube/03d59ba2943f5a0c7a3ea946fe199279457557.png',
                'https://p0.meituan.net/travelcube/1d2283db8adfbd7b1d3c48d31da0da62717653.png'
            ]
        }
    },
    mounted() {
        this.startCarousel()

    },
    beforeUnmount() {
        this.stopCarousel()

    },
    methods: {
        nextPage() {
            this.ActivePage++;
                if(this.ActivePage >= this.catergorySelection.length ){
                    this.ActivePage = 0 ;
                }
        },
        startCarousel(){
            this.carouselInterval = setInterval(this.nextPage, 3000);
        },
        restartCarousel(){
            this.startCarousel();
        },
        stopCarousel() {
            clearInterval(this.carouselInterval); 
        },
        setActivePage(idx) {
        this.ActivePage = idx;
        this.stopCarousel();
        },

    }
}
</script>

<style scoped>
.mainPart2{
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    background-color: white;

    height: 60rem;
}

.TitleIntroduction{
    position: relative;
    top: 9rem;
    display: flex;
    width: 15rem;
    height: 10rem;
    justify-content: center;
    align-items: center;
    box-sizing: border-box;
    opacity: 0;
    transform: translateY(4rem);
    transition: 0.5s;
}

.TitleIntroduction.enter{
    opacity: 1;
    transform: translateY(0);
}

.ServiceTitle{
    height: 7rem;
    width: 25rem;
}

.showPart{
    display: flex;
    flex-direction: row;
    height: 50rem;
    width: 60%;
    box-sizing: border-box;
    opacity: 0;
    transform: translateY(4rem);
    transition: all 0.5s;

}
.showPart.enter{
    opacity: 1;
    transform: translateY(0);
}

.SelectPart{
    display: flex;
    flex-direction: column;
    width: 60%;
    box-sizing: border-box;
    padding: 10rem 4rem;
    gap:0rem
}

.head{
    font-size: 2.5rem;
    font-weight:500;
}


.catergory{
    display: flex;
    flex-direction: row;
    align-items: center;
    height: 8rem;
    transition: all 0.5s ease;
}


.catergory.selectionActive,
.catergory:hover{
    color: rgb(255,186,30);

}

.iconframe{
    position: relative;
    display: flex;
    align-items: center;
    width: 4rem;
    height: 4rem;
    box-sizing: border-box;
}

.iconframe > .unSelected{
    position: absolute;
    opacity: 1;
    height:2.5rem;
    width: 2.5rem;
    transition: all 0.5s ease;
}

.iconframe >.unSelected.active{
    opacity: 0;
}
.iconframe > .selected{
    position: absolute;
    opacity: 0;
    height:2.5rem;
    width: 2.5rem;
    transition: all 0.5s ease;
}

.iconframe > .selected.active{
    opacity: 1;
}

.textFrame{
    display: flex;
    flex-direction: column;
    height: 6rem;
    box-sizing: border-box;
}

.mainText{
    position: relative;
    flex: 2;
    display: flex;
    flex-direction: row;
    align-items:flex-end;
    font-size: 1.5rem;
    transition: all 0.5s;
}

.mainText::after{
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 8rem;
    height: 0.25rem;
    background-color: rgb(255, 189, 39); 
    opacity: 0;
    transition: all 0.5s;
    
}

.mainText.active,
.mainText.active::after{
    align-items: center;
    font-size: 2rem;
    color: rgb(255, 189, 39); 
    opacity: 1;
}
.subText{
    flex: 1;
    display: flex;
    align-items: flex-end;
    font-size: 0.85rem;
    color: rgb(196,196,196);
    transition: all 0.5s;
}
.subText.active{
    color: rgb(255,186,30);
}
.viewPart {
    display: flex;
    width: 50%;
    box-sizing: border-box;
    padding: 10rem 4rem;
    justify-content: center;
    align-items: center;
    position: relative; 
    opacity: 0;
    transform: translateY(4rem);
    transition: all 0.5s;
}

.viewPart.enter {
    opacity: 1;
    transform: translateY(0);
}

.phoneEdge{
    z-index: 0;
    position: absolute;
    bottom: -1.75rem;
    right: 4.25rem;
    height: 44rem;
    object-fit: contain; 

}
.phonePage{
    position: absolute;
    height: 42rem;
    bottom: -0.75rem;
    right: 5.25rem;
    object-fit: contain; 
    z-index: 1;
    opacity: 0;
    transition: all 0.5s ease;
}

.phonePage.active{
    opacity: 1;
}
</style>