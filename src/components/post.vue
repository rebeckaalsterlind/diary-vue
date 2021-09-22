<template>

    <form @submit="onSubmit">
      Title: <input type="text" placeholder="Title" id="title">
      Date: <input type="date" id="date"> <br />

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