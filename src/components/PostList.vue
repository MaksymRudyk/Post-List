<template>
  <div v-if="posts.length > 0">
    <h2 class="posts-title">Posts</h2>
    <Post-item
        v-for="post in posts"
        :key="post.id"
        :post="post"
        @remove="this.$emit('remove', post)"
    ></Post-item>
  </div>
  <h2 style="color: red; text-align: center;" v-else>
    Post List is empty
  </h2>
</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  components: {
    PostItem
  },
  props: {
    posts: {
      type: Array,
      require: true
    }
  }
}
</script>

<style scoped>
  .posts-title {
    text-align: center;
  }
</style>