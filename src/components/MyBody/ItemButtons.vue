<template>
 <div class="item__buttons">
   <my-button
       class="button card__back"
       :disabled="status === 'План'"
       @click="movePost(postId, -1)"
   >
     &lt;-
   </my-button>
   <my-button class="button post__edit" @click="showDialog">
     Edit
   </my-button>
   <my-button class="button post__last" @click="movePost(postId, +1)">
     {{ status === 'Готово' ? 'X' : '->' }}
   </my-button>
 </div>
</template>

<script>
import MyButton from "@/App";
export default {
  name: "ItemButtons",
  components: {MyButton},
  data() {
    return {
      lastButtonValue: '->',
    }
  },
  props:{
    showDialog: Function,
    postId: Number,
    status: String,
    movePost: Function,
    postBody: String,
    postPriority: Number,
    dialogVisible: Boolean,
    handleModal: Function,
  },

}
</script>

<style scoped>
.item__buttons{
  display: contents;
  justify-content: space-between;
}
</style>