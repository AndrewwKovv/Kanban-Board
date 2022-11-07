<template>
  <div class="item__buttons" >
    <my-button
       class="button card__back"
       :disabled="status === 'План'"
       @click="movePost(postId, -1)"
    >
    &lt;
    </my-button>
    <my-button class="button post__edit" @click="showDialog"
    >
     Edit
    </my-button>
    <my-button class="button post__next" @click="movePost(postId, +1)"
    >
     {{ status === 'Готово' ? 'X' : '>' }}
    </my-button>
  </div>
  <my-dialog
      v-model:show="dialogVisible"
      :id="postId"
      :body="postBody"
      :priority="postPriority"
      :handleModal="handleModal" />

</template>

<script>

import MyDialog from "@/components/UI/MyDialog";
import MyButton from "@/components/UI/MyButton";

export default {
  name: "item-buttons",
  components: {MyButton, MyDialog},
  data() {
    return {
      dialogVisible: false,
    }
  },
  props:{
    postId: Number,
    status: String,
    movePost: Function,
    postBody: String,
    postPriority: Number,
    handleModal: Function,
  },
  methods:{
    showDialog(){
      this.dialogVisible = true;
    },
  },

}
</script>

<style scoped>
.item__buttons{
  display: contents;
  justify-content: space-between;
}
.button {
  background-color: var(--secondary-color);
  border: 2px solid dodgerblue;
  padding: 0;
  width: 40px;
  height: 40px;
  border-radius: 5px;
  text-align: center;
}
</style>