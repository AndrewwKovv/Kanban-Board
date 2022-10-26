<template>
  <div v-if="posts.length > 0" class="post__list">
    <h3></h3>
    <post-item
        v-for="post in posts"
        :post = "post"
        :key="post.id"
        @remove="$emit('remove',post)"
    >
    </post-item>
  </div>
  <h2 v-else style="color: dodgerblue; text-align: center; margin-top: 20px;">
  А тут пусто теперь
  </h2>
</template>

<script>
import PostItem from "@/components/MyBody/PostItem";
export default {
  components: {PostItem},
  props:{
    posts:{
      type: Array,
      required: true
    }
  },
  name: "PostList"
}
</script>

<style scoped>
.post__list{
  padding: 20px 150px;
}
</style>