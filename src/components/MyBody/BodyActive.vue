<template>
  <div class="body__wrapper">
    <my-button
        @click="showDialog"
        class="body__btn"
    >
      Создать задачу
    </my-button>
    <my-dialog
        body=''
        :priority="1"
        :id="0"
        :handleDial="handleDial"
        v-model:show="dialogVisible"
        />
      <board-list
          :posts="posts"
          :statuses="statuses"
          :movePost="movePost"
          :handleDial="handleDial"

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
    handleDial: Function
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
  display: grid;
  transition: 0.4s;
  background-color: var(--body-background);
  width: 100%;
  margin: auto;
}

.body__btn{
  margin: 15px 150px;
  width: 150px;
  height: 35px
}
@media (max-width: 762px) {
  .body__btn {

    margin: 15px 15px;

  }
}
</style>