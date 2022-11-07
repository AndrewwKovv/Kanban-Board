<template>
  <div class="board__wrapper">
    <post-list
        v-for="(status, key, index) in statuses"
        :key="index"
        :posts="filteredPosts(posts, status)"
        :boardId="index"
        :movePost="movePost"
        :handleDial="handleDial"
    >


    </post-list>
  </div>
</template>

<script>
import PostList from "@/components/MyBody/PostList";
export default {
  name: "board-list",
  components: {PostList},
  props:{
    posts: Object,
    statuses: Object,
    movePost: Function,
    handleDial: Function,


  },
  methods:{
    filteredPosts(posts, postId) {
      return this.posts.filter((post) => postId.includes(post.id))
    },
  },

}
</script>

<style scoped>
.board__wrapper{
  padding: 20px 150px;
  width: 100%;
  display: flex;
  gap: 20px;
}
@media (max-width: 930px) {
  .board__wrapper {
    flex-direction: column;
    padding: 20px 15px;

  }
}

</style>