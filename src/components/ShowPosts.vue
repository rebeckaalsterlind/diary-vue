<template>

  <div>
    <h2>All posts</h2>
    <ul>
      <li v-for="post in diary" :key="post.date" v-on:click="showContent(post)">{{post.date}} | {{post.title}}</li>
    </ul> 
    <div class="post" v-if="post !== null">
      <h3>{{post.title}} {{post.date}}</h3>
      {{post.content}}
    </div >
  </div>
</template>

<script>


export default {
  name: "ShowPosts",
  
  props: {
    diary: {
      type: Array    
    }
  },

  data() {
    return {
      post: null
    }
  },

  methods: {
    showContent(post) {
      this.post = post;
    }

  },

  created() {
    console.log('created in showpost');
  },

  mounted() {
    console.log('mounted in shoppost');
  },

  updated() {
    console.log('updated in showpost')
  }


}

</script>

<style>
  .post {
    border: 2px solid black;
  }
</style>