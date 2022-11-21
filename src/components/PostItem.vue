<template>
  <div class="post">
    <div>
      <div><strong>Name: </strong> {{ post.title }}</div>
      <div><strong>Description:</strong> {{ post.body }}</div>
    </div>
    <div class="post__buttons">
      <my-button class="post__delete-btn" @click="deletePost">Delete</my-button>
    </div>
  </div>
</template>

<script>
import MyButton from "@/components/UI/Mybutton";
export default {
  components: {MyButton},
  props: {
    post: {
      type: Object,
      require: true
    }
  },

  methods: {
    deletePost() {
      const post = this.post
      this.$emit('remove', post)
    }
  }
}
</script>

<style scoped>
  .post {
    min-height: 100px;
    border: solid 3px teal;
    border-radius: 10px;
    margin: 10px 10px;
    padding: 5px 5px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .post__delete-btn {
    color: red;
    border: 1px solid red;
  }
</style>