<template>
  <div class="app">
    <h1>The page of posts</h1>
    <my-button
      style="margin: 15px 0; border: 2px solid orange; color: orange"
      @click="showDialog"
    >
      Create post
    </my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form
      @create="createPost"
    />
    </my-dialog>
    <post-list
      :posts="posts"
      @remove="removePost"
    />
  </div>
</template>

<script>
import PostForm from './components/PostForm';
import PostList from '@/components/PostList';
import MyDialog from './components/UI/MyDialog.vue';

export default {
  components: {
    PostForm,
    PostList,
    MyDialog
  },

  data() {
    return {
      posts: [
        { id: 1, title: 'Javascript 1', body: 'Description of the post 1' },
        { id: 2, title: 'Javascript 2', body: 'Description of the post 2' },
        { id: 3, title: 'Javascript 3', body: 'Description of the post 3' },
      ],
      dialogVisible: false,
    };
  },

  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Comic Sans MS', cursive;
}

.app {
  padding: 20px;
}

</style>

