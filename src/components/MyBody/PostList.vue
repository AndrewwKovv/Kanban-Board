<template>
  <div v-if="posts.length > 0" class="post__list" :id="boardId">
    <div class="post__wrapper">
      <h2 class="post__title">
        {{ statusesName[boardId] }} ({{ posts.length }})
      </h2>
      <post-item
          v-for="post in posts"
          :key="post.id"
          :post = "post"
          :status="statusesName[boardId]"
          :movePost="movePost"
          :dialogVisible="dialogVisible"
          :showDialog="showDialog"
          :handleModal="handleModal"

      >
      </post-item>
    </div>
  </div>

</template>

<script>
import PostItem from "@/components/MyBody/PostItem";
export default {
  components: {PostItem},
  data() {
    return {
      statusesName: ['План', 'В работе', 'Готово'],
    }
  },
  props:{
    posts:{
      type: Array,
      required: true,
    },
    showDialog: Function,
    boardId: Number,
    movePost: Function,
    handleModal: Function,
    dialogVisible: Boolean,
  },
  name: "PostList"
}
</script>

<style scoped>
.post__list{
  display: flex;
  justify-content: space-between;
  padding: 20px;
  height: 100vh;
}
.post__wrapper{
  padding: 20px;
  background-color: var(--secondary-color);


}
.post__title{
  text-align: center;
  color: dodgerblue;
}
</style>