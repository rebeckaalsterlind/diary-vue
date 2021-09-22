<template>
  <div id="app">
 
    <h2>Hej {{newPost.title}}</h2>
    <h4>Du har klickat {{clicked}} gånger på knappen</h4>
    <button @click="onClick" >Click me!</button>

    <div v-if="clicked >= 5">
      Nu får du sluta klicka!
    </div>

    <Post :newPost="newPost" @save="onSubmit"/>
 
  </div>
</template>

<script>

import Post from "./components/Post.vue"

export default {
  name: 'App',
  
  data() {
    let getPost = JSON.parse(localStorage.getItem('allPosts'));

    if(getPost === null) {
      getPost = {title: ""}
    }
   
    return {
      newPost: { title: getPost.title, date: getPost.date },
      clicked: 0
    }

  },
  
  components: { Post },

  methods: {
    onClick() {
      this.clicked ++;
    },
    onSubmit(evt) {
      evt.preventDefault();

      let newPost = {"title": evt.target.title.value, "date": evt.target.date.value};
      let allPosts;
      
      if( localStorage.getItem("allPosts") !== null) {
        allPosts = JSON.parse(localStorage.getItem("allPosts"))
      } else {
        allPosts = [];
      }

      allPosts.push(newPost)
      localStorage.setItem('allPosts', JSON.stringify(allPosts)); 

    }
  }

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
