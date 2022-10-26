<template>
  <div class="post">
    <div class="post__text">
      <div><strong>Задача №{{}}</strong></div>
      <div><strong>Описание: </strong>{{ post.title }}</div>
    </div>
    <div class="post__btns">
      <my-button @click="$emit('remove', post)">
        x
      </my-button>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    post:{
      type: Object,
      required: true,
    }
  },
  name: "PostItem"
}
</script>

<style scoped>
.post{
  margin: 15px 0;
  padding: 15px;
  border: 2px solid dodgerblue;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.post__text{
  color: dodgerblue;
}
</style>