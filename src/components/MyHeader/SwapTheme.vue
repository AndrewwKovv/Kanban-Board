<template>
  <div class="switch-wrapper" :style="themeStyle">
    <label class="switch">
      <span class="on">ON</span>
      <span class="off">OFF</span>
      <input type="checkbox" v-model="theme" @click="changeTheme">
      <span class="slider round"></span>
    </label>
  </div>
</template>

<script>
export default {
  name: "swap-theme",
  props: {
    theme: Boolean,
    changeTheme: Function,
    themeStyle: Object,
  }
}
</script>

<style scoped>
switch-wrapper {
  height: 30px;
  display: flex;
  align-items: center;
}
.on,
.off {
  -moz-user-select: none;
  -khtml-user-select: none;
  user-select: none;
  cursor: pointer;
  position: relative;
  z-index: 100;
  top: 7px;
  font-size: 13px;
}
.off {
  left: 31px;
}
.on {
  left: 7px;
}
.switch {
  position: relative;
  display: inline-block;
  width: 80px;
  height: 34px;
}
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}
.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: var(--switcher-background-color);
  -webkit-transition: .4s;
  transition: .4s;
}
.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: var(--main-color__text);
  -webkit-transition: .4s;
  transition: .4s;
}
input:checked+.slider {
  background-color: var(--switcher-background-color);
}
input:checked+.slider:before {
  -webkit-transform: translateX(45px);
  -ms-transform: translateX(45px);
  transform: translateX(45px);
}
.slider.round {
  border-radius: 34px;
}
.slider.round:before {
  border-radius: 50%;
}

</style>