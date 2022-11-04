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
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "my-dialog",

  props: {
    show: {
      type: Boolean,
      default: false,
    },



  },

  methods:{
    hideDialog(){
      this.$emit('update:show', false)
    },
    closeModal() {
      this.$emit('update:show', false)
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

</style>