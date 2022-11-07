<template>
  <div class="body__wrapper">
    <my-button
        @click="showDialog"
        style="margin: 15px 150px; width: 150px;height: 35px"
    >
      Создать задачу
    </my-button>
    <my-dialog
        body=''
        :priority="1"
        :id="0"
        :handleModal="handleModal"
        v-model:show="dialogVisible"
        />
      <board-list
          :posts="posts"
          :statuses="statuses"
          :movePost="movePost"
          :handleModal="handleModal"

      />
  </div>
</template>

<script>

import BoardList from "@/components/MyBody/BoardList";
import MyButton from "@/components/UI/MyButton";
import MyDialog from "@/components/UI/MyDialog";

export default {
  name: "body-active",
  components: { MyDialog, MyButton, BoardList},
  data(){
    return{
      dialogVisible: false,
    }
  },

  props:{
    posts: Object,
    statuses: Object,
    movePost: Function,
    handleModal: Function
  },
  methods:{
    showDialog(){
      this.dialogVisible = true;
    },
  },

}
</script>

<style scoped>
.body__wrapper{
  position: relative;
  transition: 0.4s;
  height: 100vh;

}
</style>