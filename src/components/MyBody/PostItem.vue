<template>
  <div class="post">
    <div>
      <div><strong>Задача №{{ post.title }}</strong></div>
      <div><strong>Описание: </strong>{{ post.body }}</div>
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
</style>