<template>
  <div>
    <h3>List of users</h3>
    <post-item
      v-for="post of posts"
      :post="post"
      :key="post.id"
    />
  </div>
</template>

<script>
import PostItem from '@/components/PostItem';
export default {
  components: {PostItem},
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




