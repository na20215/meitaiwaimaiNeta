<template>
  <div class="block">
    <slot></slot>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.block{
    flex:1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100%;
    cursor: pointer;
    gap:0.85rem;
}

.block:hover{
    height: 110%;
}
</style>