<template>
  <div class="post">
    <div class="post__text">
      <div class="post__head">
        <h3><strong>
          Задача №{{ post.id }}
        </strong></h3>
        <span class="post__priority" :class="postPriority">
          {{ post.priority }}
        </span>
      </div>
      <p>{{ post.body }}</p>
      <p>{{ formateDate(post.data) }}</p>
    </div>
    <div class="post__btns">
      <item-buttons
          :movePost="movePost"
          :status="status"
          :postId="post.id"
          :postBody="post.body"
          :postPriority="post.priority"
          :dialogVisible="dialogVisible"
          :showDialog="showDialog"
          :handleModal="handleModal"
    />
    </div>
  </div>
</template>

<script>
import ItemButtons from "@/components/MyBody/ItemButtons";
export default {
  components: {ItemButtons},
  props:{
    post: Object,
    movePost: Function,
    status: String,
    dialogVisible: Boolean,
    showDialog: Function,
    handleModal: Function,
  },
  methods:{
    formateDate(date) {
      const year = date.getFullYear()
      const month = date.getMonth() + 1
      const _date = date.getDate()
      const time = String(date).slice(16, 25)
      const formatted = `${
          _date.toString().length === 1 ? '0' + _date : _date
      }.${
          month.toString().length === 1 ? '0' + month : month
      }.${year} ${time}`
      return formatted
    },
  },
  computed: {
    postPriority() {
      return 'post__priority_' + String(this.post.priority)
    },
  },
  name: "PostItem"
}
</script>

<style scoped>
.post{
  background-color: var(--content-background);
  margin: 15px 0;
  padding: 15px;
  border: 2px solid dodgerblue;
  align-items: center;

}
.post__head{
  display: flex;
  justify-content: space-between;
}
.post__text{
  color: dodgerblue;
}
.post__btns{
  display: flex;
  justify-content: space-between;
}
.post__priority {
  width: 22px;
  height: 22px;
  border: 1px solid var(--main-color);
  border-radius: 100%;
  text-align: center;
  line-height: 20px;
  transition: 0.4s;
  color: var(--main-color);
}
.post__priority_1 {
  background-color: #fea3a2;
}
.post__priority_2 {
  background-color: #fffc9e;
}
.post__priority_3 {
  background-color: #adecc7;
}

</style>