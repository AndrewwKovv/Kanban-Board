<template>
  <div class="footer__wrapper">
    <p>
      Ковшов Андрей 211-321
    </p>
    <a href="#" class="footer__up">
      Наверх
    </a>
  </div>
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
  background: aliceblue;
  padding: 20px 100px;
  color: dodgerblue;
}
.footer__up{
  color: dodgerblue;
  text-decoration: none;
}
</style>