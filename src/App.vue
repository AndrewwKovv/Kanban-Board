<template>
  <div class="app" :style="themeStyle">
    <header-active :theme="theme" :changeTheme="() => theme = !theme" />
    <body-active
        :statuses="statuses"
        :posts="posts"
        :movePost="movePost"
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


 export default {
   components:{
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
       theme: false,
     }
   },
   methods: {
     handleModal(body, priority, postId) {
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
             console.log(post)
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
         const statusArr = Object.values(this.statuses[status])
         if (statusArr.includes(id)) {
           this.statuses[status] = statusArr.filter( (statusId) => statusId !== id )
           statusIndex = index + direction
         }
       })
       if (statusIndex === Object.keys(this.statuses).length) {
         return
       }

       this.statuses[keys[statusIndex]].push(id)
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
             '--btn-color': '#1E90FFFF',
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
             '--btn-color': '#FFFFFF',
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