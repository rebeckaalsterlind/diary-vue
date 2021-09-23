<template>

    <form @submit="onSubmit">
      Title: <input type="text" placeholder="Title" id="title" required><br />
      Date: <input type="date" id="date"> <br />
      <textarea id="content" rows="8" cols="30" maxlength="200" required /><br />
      <button>Save</button>
    </form>
  
</template>

<script>

  export default {
    name: "Post",
    
    props: {
      newPost: {
        type: Object
      }
    },
    methods: {
      onSubmit(evt) {
        this.$emit("save", evt);
      }
    }

  }

</script>

<style>

</style>