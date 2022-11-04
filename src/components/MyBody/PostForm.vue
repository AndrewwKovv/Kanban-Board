<template>
  <form @submit.prevent class="dialog__form">
    Описание
    <my-input
        class="content__form"
        v-model="post.body"
        type="text"
        placeholder="Описание"
    />
    Приоритет
    <select
        v-model="post.priority"
        class="modal-post-input"
    >
      <option>1</option>
      <option>2</option>
      <option>3</option>
    </select>
    <my-button
        class="btn__save"
        @click="onClick"
    >Сохранить</my-button>
  </form>
</template>

<script>
import MyButton from "@/components/UI/MyButton";
import MyInput from "@/components/UI/MyInput";
export default {
  components: {MyInput, MyButton},
  props: {
    body: String,
    priority: Number,
    id: Number,
    handleModal: Function,
    show: {
      type: Boolean,
      default: false,
    },
  },
  data(){
    return{
      post: {
        body: this.body,
        priority: this.priority,
        id: Number(this.id),
      },
    }
  },

  methods:{
    onClick() {

      this.handleModal(this.post.body, this.post.priority,this.post.id)
      this.$emit('update:show', false)

    },
  },
  name: "post-form"
}
</script>

<style scoped>
form{

  display: flex;
  flex-direction: column;
}
.modal-post-input{
  margin: 5px 0;
  height: 37px;
  width: 100%;
  border: 1px solid dodgerblue;
  color: var(--board-text);
  background-color: var(--secondary-color);
  padding: 0 10px;
}
.content__form{
  background-color: var(--secondary-color);
  margin-bottom: 20px;
}
.dialog__form{
  color: dodgerblue;
}
.btn__save{
  align-self: center;
  margin-top: 60px;
  background-color: var(--main-color);
  color: white;
  border-radius: 5px;
}
</style>