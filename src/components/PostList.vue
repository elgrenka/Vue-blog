<template>
  <div class="post" v-for="post of posts" :key=post.id>
    <div><b>Name: </b>{{ post.title }}</div>
    <div><b>Description: </b>{{ post.body }}</div>
  </div>
</template>

<script>
  export default {
    props: {
      posts: {
        type: Array,
        required: true
      }
    }
  };
</script>

<style scoped>
.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}
</style>



