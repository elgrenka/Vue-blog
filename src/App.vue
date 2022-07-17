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
      <post-form @create="createPost" />
    </my-dialog>

    <post-list :posts="posts" @remove="removePost" v-if="!isPostLoading" />
    <div v-else>Loading ...</div>
  </div>
</template>

<script>
import PostForm from "./components/PostForm";
import PostList from "@/components/PostList";
import MyDialog from "./components/UI/MyDialog.vue";
import axios from "axios";

export default {
  components: {
    PostForm,
    PostList,
    MyDialog,
  },

  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostLoading: false,
    };
  },

  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostLoading = true;
          const response = await axios.get(
            "https://jsonplaceholder.typicode.com/posts?_limit=10"
          );
          this.posts = response.data;
      } catch (error) {
        alert("Somthing wrong");
      } finally {
        this.isPostLoading = false;
      }
    },
  },
  mounted() {
    this.fetchPosts();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Comic Sans MS", cursive;
}

.app {
  padding: 20px;
}
</style>

