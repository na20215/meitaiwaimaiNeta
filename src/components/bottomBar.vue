<template>
  <div class="BottomPart">
    <div class="part1">
        <div class="partLeft">
            <a>技术合作中心</a>
            <a>常见问题</a>
            <a>媒体报道</a>
            <a>用户反馈</a>
            <a>资质规则</a>
            <a>诚信举报</a>
            <a>入驻加盟</a>
            <a>加入我们</a>
            <a>KeeTa外卖</a>
        </div>
        <div class="otherPart">
            <div class="partMid">
                <h3>品牌合作</h3>
                <span>wpbg.marketing@meituan.com</span>
                <h3>更多商家，更多优惠</h3>
                <span>客服 1010-9777</span>
                <span>客服不受理商务合作</span>
            </div>
            <div class="partRight">
                <h3>更多商家，更多优惠</h3>
                <div class="QRcodePart">
                    <img class="QRCode" src="../assets/38.webp">
                    <img class="QRCode" src="../assets/39.webp">
                </div>
            </div>
        </div>
    </div>
    <div class="part2">
        <span class="botinfo"><img src="../assets/32.png" :style="{height:'1.25rem',width:'1.25rem'}">北京三快科技有限公司</span>
        <span class="botinfo" >©️ meituan.com 京ICP证070791号  <a class="botinfo" href="https://beian.miit.gov.cn/">京ICP备10211739号-1</a></span>
        
        <a class="botinfo" href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=11000002002052"><img src="../assets/33.png">京公网安备 11000002002052号</a>
    </div>
</div>
  
</template>

<script>
export default {

}
</script>

<style scoped>
 .BottomPart{
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 22.5rem;
    padding: 0%;
    margin: 0%;
    gap:1px;
    background-color: rgb(102,102,102);
 }
 .part1{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 5rem;
    padding: 0rem 25rem;
    box-sizing: border-box;
    height: 18.5rem;
    width: 100%;
    background-color: rgb(51,51,51);
    color: white;
 }
 .partLeft{
    display: grid;
    justify-items: center;
    align-items: center;
    grid-template-columns: 1fr 1fr;
    padding: 4rem 0rem;
    gap: 0rem 1rem;
    height: 100%;
    margin-right: 15rem;
    color: rgb(143,170,170);
    box-sizing: border-box;
 }

 .partLeft > a {
    font-size: 0.85rem;
 }

 .otherPart{
    display: flex;
    flex-direction: row;
    height: 100%;
    width: 25rem;
    gap: 3rem;
 }
 .QRcodePart{
    display: flex;
    flex-direction: row;
    gap: 1rem;
 }
 .QRCode{
    height: 5.625rem;
    width: 5.625rem;
 }
 .partMid{
    display: flex;
    flex-direction: column;
    justify-content:center ;
    height: 100%;
 }
 .partRight{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100%;
 }
 .part2{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;

    gap: 5rem;
    box-sizing: border-box;
    background-color: rgb(51,51,51);
    height: 4rem;
    width: 100%;
 }

 .part2 > .botinfo{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    color:rgb(127,127,127);
    font-size: 0.75rem;
    gap:0.5rem;
 }
</style>