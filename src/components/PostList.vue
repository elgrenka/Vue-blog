<template>
  <div>
    <h3>List of posts</h3>
    <!-- <div v-if="posts.length > 0"> --> 
    <div v-show="posts.length > 0">
      <post-item
        v-for="post of posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
      />
    </div>
    <h4
      v-show="posts.length === 0"
      style="color: crimson; margin-top: 15px"
    >
      ... is empty! Add the post!
    </h4>
  </div>
</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
</style>




