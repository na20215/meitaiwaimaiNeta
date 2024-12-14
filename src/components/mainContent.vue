<template>
  <div class="root">
    <main-part-1></main-part-1>
    <main-part-2 ref="part2"></main-part-2>
    <main-part-3 ref="part3"></main-part-3>
    <main-part-4 ref="part4"></main-part-4>
    <side-bar></side-bar>
  </div>

</template>

<script>
import MainPart1 from './mainContent/mainPart1.vue'
import MainPart2 from './mainContent/mainPart2.vue'
import MainPart3 from './mainContent/mainPart3.vue'
import MainPart4 from './mainContent/mainPart4.vue'
import SideBar from './mainContent/sideBar.vue'
export default {
  components: { MainPart1, MainPart2, MainPart3, MainPart4, SideBar },
    methods: {
        createIntersectionObserver() {
            const options = {
                root: null,
                threshold: 0.4
            };
            const observer = new IntersectionObserver(this.handleIntersection, options);
            
            observer.observe(this.$refs.part2.$refs.header);
            observer.observe(this.$refs.part2.$refs.viewAnime);
            observer.observe(this.$refs.part2.$refs.title);
            observer.observe(this.$refs.part3.$refs.header);
            observer.observe(this.$refs.part3.$refs.main);
            observer.observe(this.$refs.part4.$refs.header);
            observer.observe(this.$refs.part4.$refs.main);
            // this.$refs.part2.$refs.selection.forEach(selection => observer.observe(selection));
            
        },
        destroyIntersectionObserver() {
            if (this.observer) {
                this.observer.disconnect();
            }else {
                console.error("header element not found");
            }
        },
        handleIntersection(entries) {
            entries.forEach(entry => {
                const { top } = entry.boundingClientRect;
               
                if(entry.isIntersecting){
                        entry.target.classList.add('enter');
                } 
                if (!entry.isIntersecting && top >= (window.innerHeight * 0.5)) {
                        entry.target.classList.remove('enter');
                }

            });
        }
    },
    mounted() {
        this.createIntersectionObserver();
    },
    beforeUnmount() {
        this.destroyIntersectionObserver();
    },
}
</script>

<style scoped>
.root{
    position: relative;
    display: flex;
    flex-direction: column;
    height: auto;
    width: 100%;
}

</style>