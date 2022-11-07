<template>
  <div class="post__list" :id="boardId" @drop="onDrop" @dragover.prevent @dragenter.prevent>
    <h2 class="post__title">
      {{ statusesName[boardId] }} ({{ posts.length }})
    </h2>
    <post-item
        v-for="post in posts"
        :key="post.id"
        :post = "post"
        :status="statusesName[boardId]"
        :movePost="movePost"
        :handleModal="handleModal"
    >
    </post-item>

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
    posts: Object,
    boardId: Number,
    movePost: Function,
    handleModal: Function,
  },
  methods:{
    onDrop(e) {
      const postId = +e.dataTransfer.getData('itemId');
      const ancientBoardId = +e.dataTransfer.getData('boardId');
      const direction = this.boardId - ancientBoardId;
      this.movePost(postId, direction);
    },
  },
  name: "post-list"
}
</script>

<style scoped>
.post__list{
  transition: 0.4s;
  width: 100%;
  justify-content: space-between;
  padding: 20px;
  background-color: var(--secondary-color);
  min-height: 550px;
}

.post__title{
  text-align: center;
  color: dodgerblue;
}
</style>