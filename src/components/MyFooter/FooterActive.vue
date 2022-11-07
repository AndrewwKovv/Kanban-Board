<template>
  <footer class="footer__wrapper">
    <p class="footer__parag">
      Ковшов Андрей 211-321
    </p>
    <a href="#" class="footer__up">
      &#8657;
    </a>
  </footer>
</template>

<script>
export default {
  name: "footer-active"
}
</script>

<style scoped>
.footer__wrapper{
  display: flex;
  justify-content: space-between;
  padding: 20px 100px;
  color: var(--board-text);
  background-color: var(--secondary-color);
  transition: 0.4s;
}
.footer__parag{
  padding:9px 0;
}
.footer__up{
  padding: 7px;
  text-decoration: none;
  border: 1px solid dodgerblue;
  width: 40px;
  height: 40px;
  border-radius: 5px;
  text-align: center;
}
.footer__up:visited {
  color: var(--board-text);
}
</style>