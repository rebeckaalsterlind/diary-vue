<template>
  <div id="app">
 
    <h2>Hej {{user.firstName}}</h2>
    <h4>Du har klickat {{clicked}} gånger på knappen</h4>
    <button @click="onClick" >Click me!</button>

    <div v-if="clicked >= 5">
      Nu får du sluta klicka!
    </div>
    <Post />
 
  </div>
</template>

<script>

import Post from './components/post.vue';

export default {
  name: 'App',
  
  data() {
    return {
    user: { firstName: localStorage.getItem("firstName"), lastName: localStorage.getItem("lastName") },
    clicked: 0
    }
  },
  
  components: { Post },

  methods: {
    onClick() {
      console.log('clickat på knapp')
      this.clicked ++;
    },
    onSubmit(evt) {
      evt.preventDefault();
      console.log('form saved', evt.target.firstName.value)
      localStorage.setItem("firstName", evt.target.firstName.value)
      localStorage.setItem("lastName", evt.target.lastName.value)
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
