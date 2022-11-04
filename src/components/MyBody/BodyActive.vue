<template>
  <div class="body__wrapper">
      <board-list
          :posts="posts"
          :statuses="statuses"
          :movePost="movePost"
          :dialogVisible="dialogVisible"
          :showDialog="showDialog"
          :handleModal="handleModal"

      />
  </div>
</template>

<script>

import BoardList from "@/components/MyBody/BoardList";

export default {
  name: "body-active",
  components: {BoardList},


  props:{
    posts: {
      type: Object,
    },
    statuses: Object,
    movePost: Function,
    dialogVisible: Boolean,
    showDialog: Function,
    handleModal: Function



  },

}
</script>

<style scoped>
.body__wrapper{

}
</style>