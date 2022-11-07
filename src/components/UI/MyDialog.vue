<template>
  <div class="dialog" v-if="show" @click="hideDialog">
    <div class="dialog__content" @click.stop>
      <div class="form__close">
        <my-button
            class="form__btns"
            @click.self="closeModal"
        >
          X
        </my-button>
      </div>
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
      </form>
      <div class="dialog__btn">
        <my-button
            class="btn__save"
            @click="onClick"
        >Сохранить</my-button>
      </div>
    </div>
  </div>
</template>

<script>
import MyButton from "@/components/UI/MyButton";
import MyInput from "@/components/UI/MyInput";
export default {
  name: "my-dialog",
  components: {MyInput, MyButton},
  props: {
    body: String,
    priority: Number,
    id: Number,
    handleModal:Function,
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
        id: this.id,
      },
      falseBody: String,

    }
  },
  methods:{
    hideDialog(){
      this.$emit('update:show', false)
    },
    closeModal() {
      this.$emit('update:show', false)
    },
    onClick() {
      this.falseBody = '';
      if(this.post.body  === this.falseBody){
        console.log('!')
      }
      else{
        this.handleModal(this.post.body, this.post.priority,this.post.id)
        this.$emit('update:show', false)
        this.post.body = ''
        this.post.priority = "1"
      }


    },
  }

}
</script>

<style scoped>
.dialog {
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);
  z-index: 999;
  position: fixed;
  display: flex;



}
.dialog__content{
  margin: auto;
  background-color: var(--content-background);
  border: 1.5px solid dodgerblue;
  border-radius: 10px;
  min-height: 170px;
  min-width: 370px;
  padding: 20px;

}
.form__close{
  width: 100%;
  text-align: right;
}
.form__btns{
  background-color: var(--secondary-color);
  border-radius: 100px;
  color: dodgerblue;
  border: 1px solid dodgerblue;
}
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
.dialog__btn{
  width: 100%;
  text-align: center;
}
.btn__save{
  margin-top: 60px;
  background-color: var(--main-color);
  color: var(--btn-color);

  border-radius: 5px;
}


</style>