<template>
  <div class="sidebar">
    <div class="backToTop" @click="setWindowBackToTop()">
        <span>^</span>
        <span>顶部</span>
    </div>
    <span>美团外卖app</span>
    <img src="../../assets/30.png">
    <span>美团外卖小程序</span>
    <img src="../../assets/31.png">
  </div>
</template>

<script>
export default {
    methods:{
        setWindowBackToTop(){
            window.scrollTo({
                top: 0,
                behavior:'smooth',
            })
        }
    }
}
</script>

<style scoped>
.sidebar{
    position: fixed;
    bottom:2rem;
    right:-4rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 18rem;
    width: 7rem;
    background-color: white;
    transition: all 0.5s;
    box-sizing: border-box;
    padding: 0.5rem;
    font-size: 0.8rem;
    gap: 1rem;
}

.sidebar:hover{
  transform: translateX(-4rem);
}

img{
    height: 4rem;
    width: 4rem;
}


.backToTop{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 2rem;
    cursor: pointer;
    box-sizing: border-box;
    color: rgb(153,153,153);
}

.backToTop:hover{
    color:rgb(255,209,0);
    border: 0.2rem solid white;
}
</style>