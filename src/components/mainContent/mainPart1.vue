<template>
  <div class="mainPart1">
    <div class="BRYBlock">
        <tri-block 
        v-for="(Block,idx) in BRYBlockContent"
        :key="idx"
        :style="{backgroundColor: Block.backgroundColor}"
        >
        <div class="mainTitleAndIcon">
            <img :src="Block.Icon">
            <div class="mainTitle">{{ Block.mainTitle }}</div>
            <div class="arrow">></div>
        </div>
        <div class="subTitle">{{ Block.subTitle }}</div>
        
        </tri-block>

    </div>
  </div>
</template>

<script>
import TriBlock from './TriBlock.vue'
export default {
  components: { TriBlock },
  data(){
    return{
        BRYBlockContent:[
            {
                Icon:'https://p0.meituan.net/travelcube/2464977144b4febfe9ed704740fc3555962.png',
                mainTitle:'我要入驻',
                subTitle:'商家、配送、城市代理、服务市场',
                backgroundColor:'rgb(101,143,247)',
            },
            {
                Icon:'https://p1.meituan.net/travelcube/4ddfca5846d86a63aac3be7282f8462b969.png',
                mainTitle:'开发者接入',
                subTitle:'技术合作中心',
                backgroundColor:'rgb(245,76,49)',
            },
            {
                Icon:'https://p0.meituan.net/travelcube/9a6e5f5f194d6d8414d79e516e875f911440.png',
                mainTitle:'我要点外卖',
                subTitle:'快捷下单，一键点餐',
                backgroundColor:'rgb(255,189,39)',
            }    
        ]


    }
  }

}
</script>

<style scoped>
.mainPart1{
    display: flex;
    position: relative;
    width: 100%;
    background-size: cover;
    background-image: url(https://p0.meituan.net/travelcube/d2ab674fa0e4c875865e524d82fe15a34372569.png);
    height: 50rem;
    justify-content: center;
    align-items: center;
}
.BRYBlock{
    position: absolute;
    bottom: -6rem;
    display: flex;
    flex-direction: row;
    height: 10.5rem;
    width: 62.5rem;
    justify-content: center;
    align-items: center;
}
.mainTitleAndIcon{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 0.25rem;
}
.mainTitleAndIcon > img{
    width: 2.0rem;
    height: 2.0rem;
}
.mainTitleAndIcon > .mainTitle{
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 1.5rem;
}

.arrow{
    font-size: 1.5rem;
    margin-left:0.55rem;
    color: rgba(255,255,255,0.5);
}
.subTitle{
    font-size: 1rem;
    color: rgba(255,255,255,0.8);
}
</style>