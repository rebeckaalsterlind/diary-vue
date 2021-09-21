<template>

    <form @submit="onSubmit">
      <input type="text" v-model="user.firstName" id="firstName">
      <input type="text" v-model="user.lastName" id="lastName">
      <button>Save</button>
    </form>
  
</template>

<script>

  export default {
    name: "post"
  }

</script>

<style>

</style>