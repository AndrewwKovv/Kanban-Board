<template>
  <div class="app" >
    <header-active/>

    <my-button
          @click="showDialog"
          style="margin: 15px 150px"
    >
        Создать задачу
    </my-button>
    <my-dialog v-model:show="dialogVisible">
        <post-form
            @create = "createPost"
        />
    </my-dialog>

    <post-list
          :posts="posts"
          @remove="removePost"
    />

    <footer-active/>

  </div>
</template>

<script>
import PostList from "@/components/MyBody/PostList";
import PostForm from "@/components/MyBody/PostForm";
import HeaderActive from "@/components/MyHeader/HeaderActive";
import FooterActive from "@/components/MyFooter/FooterActive";

 export default {
   components:{
     FooterActive,
     HeaderActive,
     PostList, PostForm
   },
   data(){
     return{
       posts: [
         {id: 1, title: "Lorem ipsum ire", body: "Приоритет 1"},
         {id: 2, title: "lor", body: "Приоритет 1"},
         {id: 3, title: "loreb ip", body: "Приоритет 1"},
       ],
       dialogVisible:false,
     }
   },
   methods: {
    createPost(post){
      this.posts.push(post);
      this.dialogVisible = false;
    },
     removePost(post){
      this.posts = this.posts.filter(p  => p.id !== post.id)
     },
     showDialog(){
      this.dialogVisible = true;
     },

   },
   computed: {
     themeStyle() {
       switch (this.theme) {
         case true:
           return ({
             '--main-color': '#33417C',
             '--secondary-color': '#585858',
             '--main-color__text': '#ECECEC',
             '--switcher-background-color': '#0B1340',
             '--content-background': '#323332',
             '--board-text': '#ECECEC'
           })
         default:
           return ({
             '--main-color': '#2599FB',
             '--secondary-color': '#F2F9FF',
             '--main-color__text': '#FFFFFF',
             '--switcher-background-color': '#BBE0FD',
             '--content-background': "#FFFFFF",
             '--board-text': '#2599FB',
           })
       }
     },
   }
 }
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app{
  display: grid;
  grid-template-rows: auto 1fr auto;
  height: 100vh;
}

</style>