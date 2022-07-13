<template>
  <div class="app">
    <form @submit.prevent>
      <h4>Create post</h4>
      <input
        class="input"
        v-bind:value="title"
        @input="title = $event.target.value"
        type="text"
        placeholder="Name">
      <input
        class="input"
        @input="body = $event.target.value"
        type="text"
        placeholder="Description"
        v-bind:value="body">
      <button class="btn" @click="createPost">Add post</button>
    </form>
    <div class="post" v-for="post of posts" v-bind:key=post.id>
      <div><b>Name: </b>{{ post.title }}</div>
      <div><b>Description: </b>{{ post.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        { id: 1, title: 'Javascript 1', body: 'Description of the post 1' },
        { id: 2, title: 'Javascript 2', body: 'Description of the post 2' },
        { id: 3, title: 'Javascript 3', body: 'Description of the post 3' },
      ],
      title: '',
      body: ''
    };
  },
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body
      };
      this.posts.push(newPost);
      this.title = '';
      this.body = '';
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}

form {
  display: flex;
  flex-direction: column;
}

.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
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
  color: darkred;
  border: 1px solid darkred;
}
</style>

