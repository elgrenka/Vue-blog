<template>
  <div>
    <p>
     
    </p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        likes: 0,
        dislikes: 0,
      };
    },
    methods: {
      addLike() {
        this.likes++;
      },
      addDislike() {
        this.dislikes++;
      }
    }
  };
</script>

<style>

</style>

