<template>
  <header class="header__wrapper">
    <img src="@/assetLogo/HeaderLogo.svg" alt="logo" class="header__img">
    <h1 class="header__title">Kanban</h1>
    <SwapTheme :theme="theme" :changeTheme="changeTheme"/>

  </header>
</template>



<script>
import SwapTheme from "@/components/MyHeader/SwapTheme";
export default {
  name: "header-active",
  components: {SwapTheme},
  props: {
    theme: Boolean,
    changeTheme: Function,
    themeStyle: Object,
  },

}
</script>

<style scoped>
.header__wrapper{
  padding: 10px 100px;
  background-color: var(--main-color);
  display: flex;
  justify-content: space-between;
  align-items: center;

}
.header__title{
  color: white;
}
.header__img{
  height: 45px;
  width: 45px;
}

</style>