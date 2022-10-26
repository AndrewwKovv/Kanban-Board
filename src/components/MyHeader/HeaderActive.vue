<template>
  <div class="header__wrapper">
    <img src="@/assetLogo/HeaderLogo.svg" alt="logo" class="header__img">
    <h1 class="header__title">Kanban</h1>
    <swap-theme
        style="color: gray; background: aliceblue; border-radius: 20px"
    >Темная тема
    </swap-theme>
  </div> 
</template>



<script>
import SwapTheme from "@/components/MyHeader/SwapTheme";
export default {
  name: "header-active",
  components: {SwapTheme},

}
</script>

<style scoped>
.header__wrapper{
  padding: 10px 100px;
  background: dodgerblue;
  display: flex;
  justify-content: space-between;
}
.header__title{
  color: white;
}
.header__img{
  height: 45px;
  width: 45px;
}

</style>