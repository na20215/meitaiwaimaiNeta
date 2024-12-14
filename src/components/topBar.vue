<template>
  <div class="TopBar" :style="SetStyle">
    <div class="IconAndName">
            <img class="Logo" :src="SetLogoStyle()">
    </div>
    <div class="ButtonArea">
        <div 
          class="Button" 
          v-for="button in ['首页', '入驻加盟', '技术合作中心', '社会责任', '营养查询']"
          :key="button"
          :class="{ active: isActive === button }"
          @click="isActive = button"
        >
          {{ button }}
        </div>

    </div>
  </div>
</template>

<script>
export default {
    data() {
        return{
            isActive:'首页',
            isAtTop: true,
        }
    },
    computed:{
        SetStyle(){
            
            return {
                backgroundColor: this.isAtTop ? 'rgba(0,0,0,0)' : 'rgba(255, 255, 255,1)',
                color: this.isAtTop ? 'white' : 'black',
                transition: 'background-color 0.3s ease',
                
            };
        }
    },
    methods: {
        onScroll(){
            this.isAtTop = window.scrollY === 0;
        },
        SetLogoStyle(){
            return this.isAtTop ?
             require('../assets/35.webp'):
             require('../assets/36.webp');
        }
        
    },
    mounted() {
    window.addEventListener('scroll', this.onScroll);
    },
    beforeUnmount() {
    window.removeEventListener('scroll', this.onScroll);
  },
}
</script>

<style scoped>
    .TopBar{
        z-index: 999;
        display: flex;
        flex-direction: row;
        position: fixed;
        justify-content: space-evenly;
        align-items: center;
        height: 4.5rem;
        width: 100%;
        box-sizing: border-box;
    }
    .IconAndName{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        width: 12rem;
        height: 3rem;
        margin: 2rem;
        cursor: pointer;
    }

    .IconAndName > .Logo{
        height: 3rem;

    }

    .ButtonArea{
        display: flex;
        flex-direction: row;
        height: 4.5rem;
        
    }
    .ButtonArea > .Button{
        display: inline;
        position: relative;
        height:  100%;
        line-height: 4.5rem;
        padding-inline:2rem;
        text-align: center;
        margin: 0rem 1rem;
        padding:0%;
        cursor: pointer;
    }

    .ButtonArea > .Button:hover,
    .ButtonArea > .Button.active {
        font-weight: bolder;
    }
    .ButtonArea > .Button::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 0.25rem;
        background-color: rgb(255, 189, 39); 
        transform: scaleX(0); 
        transition: transform 0.1s ease-in-out;
    }

    .ButtonArea > .Button:hover::after,
    .ButtonArea > .Button.active::after {
        transform: scaleX(1);
        font-weight: bolder;
    }


</style>