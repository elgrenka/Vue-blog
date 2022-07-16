<template>
  <form @submit.prevent>
    <h4>Create post</h4>
    <input class="input" v-model="post.title" type="text" placeholder="Name">
    <input class="input" v-model="post.body" type="text" placeholder="Description">
    <button class="btn" @click="createPost">
      Add post
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    };
  },

  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post);
      this.post = {
        title: '',
        body: ''
      };
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}

.input {
  width: 100%;
  border: 1px solid blue;
  padding: 10px 15px;
  margin-top: 15px;
}

.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: red;
  border: 1px solid red;
  cursor: pointer;
}
</style>

