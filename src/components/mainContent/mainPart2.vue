<template>
  <div class="mainPart2">
    <div class="TitleIntroduction" ref="header">
        <img class="ServiceTitle" src="../../assets/37.png">
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
            <img class="phoneEdge" src="../../assets/5.png">
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
                    iconPath:require('../../assets/6.png'),
                    iconPathActive:require('../../assets/7.png'),
                },
                {
                    name:'甜品饮品 Desserts&Drinks',
                    subTitle:'幸福甜蜜',
                    iconPath:require('../../assets/8.png'),
                    iconPathActive:require('../../assets/9.png'),
                },
                {
                    name:'水果生鲜 Fresh foods',
                    subTitle:'新鲜速达',
                    iconPath:require('../../assets/10.png'),
                    iconPathActive:require('../../assets/11.png'),
                },
                {
                    name:'超市便利 SuperMarket',
                    subTitle:'优惠促销',
                    iconPath:require('../../assets/12.png'),
                    iconPathActive:require('../../assets/13.png'),
                }
            ],
            AppPage:[
                require('../../assets/14.png'),
                require('../../assets/15.png'),
                require('../../assets/16.png'),
                require('../../assets/17.png')
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