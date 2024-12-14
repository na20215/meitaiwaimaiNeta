<template>
  <top-bar></top-bar>
  <main-content></main-content>
  <bottom-bar></bottom-bar>
</template>

<script>
import BottomBar from './components/bottomBar.vue'
import mainContent from './components/mainContent.vue'
import TopBar from './components/topBar.vue'
export default {
  components: { mainContent, BottomBar, TopBar},
}
</script>

<style>
html,body{
  display: flex;
  flex-direction: column;
  justify-content: center;
  font-size: 16px;
  width: 100%;
  margin:0%;
  padding: 0%;
  overflow: auto;
  box-sizing: border-box;
}
a{
  padding: 0%;
  margin: 0%;
}
#app {
  position: relative;
  display: flex;
  flex-direction: column;
  width: 100%;
}
</style>
