<template>
  <footer class="footer__wrapper">
    <p>
      Ковшов Андрей 211-321
    </p>
    <a href="#" class="footer__up">
      Наверх
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
.footer__up{
  color: var(--board-text);
  text-decoration: none;
}
.footer__up:visited {
  color: var(--board-text);
}
</style>