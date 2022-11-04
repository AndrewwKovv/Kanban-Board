<template>
  <div class="app" :style="themeStyle">
    <header-active :theme="theme" :changeTheme="() => theme = !theme" />
    <my-button

        @click="showDialog"
        style="margin: 15px 150px; width: 150px;height: 35px"
    >
      Создать задачу
    </my-button>
    <my-dialog v-model:show="dialogVisible" >
      <post-form
          body=""
          priority="1"
          id="0"
          v-model:show="dialogVisible"
          :handleModal="handleModal"
      />
    </my-dialog>
    <body-active
        :statuses="statuses"
        :posts="posts"
        :dialogVisible="dialogVisible"
        :movePost="movePost"
        :showDialog="showDialog"
        :handleModal="handleModal"

    >
    </body-active>

    <footer-active/>

  </div>
</template>

<script>

import HeaderActive from "@/components/MyHeader/HeaderActive";
import BodyActive from "@/components/MyBody/BodyActive";
import FooterActive from "@/components/MyFooter/FooterActive";
import MyButton from "@/components/UI/MyButton";
import MyDialog from "@/components/UI/MyDialog";
import PostForm from "@/components/MyBody/PostForm";

 export default {
   components:{
     PostForm,
     MyDialog,
     MyButton,
     BodyActive,
     FooterActive,
     HeaderActive,

   },
   data(){
     return{
       newId: Number,
       posts: [
         {id: 1,
           body: "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
           data: new Date(2022, 6, 13),
           priority: 1,
         },
         {id: 2,
           body: "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
           data: new Date(2022, 8, 1),
           priority: 2,
         },
         {id: 3,
           body: "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
           data: new Date(2022, 7, 16),
           priority: 3,
         },
       ],
       statuses: {
         plan: [1],
         work: [2],
         ready: [3],
       },
       dialogVisible: false,
       theme: false,
     }
   },
   methods: {
     handleModal(body, priority, postId) {
       console.log(postId)
       switch (postId) {
         case 0:

           this.newId = 0;
           this.posts.map((obj) => {
             if (obj.id > this.newId) {
               this.newId = obj.id
             }
           })
           this.statuses.plan.push(this.newId + 1)
           this.posts.push({
             id: this.newId + 1,
             body: body,
             data: new Date(),
             priority: priority,
           })
           break
         default:

           this.posts = this.posts.map((post) => {
             if (this.post.id === postId) {
               post.body = body
               post.priority = priority
             }
             return post
           })

       }
     },
     movePost(id, direction) {
       let statusIndex
       const keys = Object.keys(this.statuses)
       keys.forEach((status, index) => {
         const statusArray = Object.values(this.statuses[status])
         if (statusArray.includes(id)) {
           this.statuses[status] = statusArray.filter( (statusId) => statusId !== id )
           statusIndex = index + direction
         }
       })
       if (statusIndex === Object.keys(this.statuses).length) {
         return
       }

       this.statuses[keys[statusIndex]].push(id)
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
             '--switcher-background-color': '#4355A1',
             '--content-background': '#323332',
             '--board-text': '#ECECEC',
             '--dialog-text': '#33417C',
             '--round-color': '#FFFFFF',
           })
         default:
           return ({
             '--main-color': '#2599FB',
             '--secondary-color': '#F2F9FF',
             '--main-color__text': '#FFFFFF',
             '--switcher-background-color': '#BBE0FD',
             '--content-background': "#FFFFFF",
             '--board-text': '#2599FB',
             '--dialog-text': '#BBE0FD',
             '--round-color': '#FFFFFF',
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
  transition: 0.4s;
  background: var(--content-background);
}

</style>