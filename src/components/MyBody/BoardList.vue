<template>
  <div class="board__wrapper">
    <post-list
        v-for="(status, key, index) in statuses"
        :key="index"
        :posts="getFilteredCards(posts, status)"
        :boardId="index"
        :movePost="movePost"
        :dialogVisible="dialogVisible"
        :showDialog="showDialog"
        :handleModal="handleModal"
    >


    </post-list>
  </div>
</template>

<script>
import PostList from "@/components/MyBody/PostList";
export default {
  name: "BoardList",
  components: {PostList},
  props:{
    posts: Object,
    statuses: Object,
    dialogVisible: Boolean,
    movePost: Function,
    showDialog: Function,
    handleModal: Function,

  },
  methods:{
    getFilteredCards(posts, ids) {
      return posts.filter((post) => ids.includes(post.id))
    },
  },

}
</script>

<style scoped>
.board__wrapper{
  display: flex;
  padding:  0 50px;
  justify-content: space-between;
}
</style>