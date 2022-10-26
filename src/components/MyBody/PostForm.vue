<template>
  <form @submit.prevent>
    <my-input
        v-model="post.title"
        type="text"
        placeholder="Описание"
    />
    <my-input
        v-model="post.body"
        type="text"
        placeholder="Приоритет"
    />
    <my-button
        style="align-self: flex-end; margin-top: 15px"
        @click="createPost"
    >Сохранить</my-button>
  </form>
</template>

<script>
export default {
  data(){
    return{
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods:{
    createPost(){
      this.post.id = Date.now();
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    }
  },
  name: "post-form"
}
</script>

<style scoped>
form{
  display: flex;
  flex-direction: column;
}
</style>