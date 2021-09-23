<template>
  <div id="app">
    <h1>My diary!</h1>
      <button v-if="!showForm" @click="showForm = true">Add new post</button>
    <ShowPosts :diary="diary" />
  
    <Post v-if="showForm" :newPost="newPost" @save="onSubmit"/>
  </div>
</template>

<script>

import Post from "./components/Post.vue";
import ShowPosts from "./components/ShowPosts.vue";

export default {
  name: 'App',  
  components: { Post, ShowPosts },
  
  data() {

    let getPost = JSON.parse(localStorage.getItem('allPosts'));
    if(getPost === null) getPost = {}
   
    return {
      newPost: { title: getPost.title, date: getPost.date, content: getPost.content },
      diary: [],
      showForm: false
    }

  },

  methods: {

    onSubmit(evt) {
      evt.preventDefault();

      let newPost = {"title": evt.target.title.value, "date": evt.target.date.value, "content": evt.target.content.value};
   
      
      if( localStorage.getItem("allPosts") !== null) {
        this.diary = JSON.parse(localStorage.getItem("allPosts"))
      } 
      
      this.diary.push(newPost)
      localStorage.setItem('allPosts', JSON.stringify(this.diary)); 

      this.showForm = false; 

    }

  },
    created() {
         if( localStorage.getItem("allPosts") !== null) {
        this.diary = JSON.parse(localStorage.getItem("allPosts"))
      } 
  },



}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
