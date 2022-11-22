<template>
  <form @submit.prevent>
    <h4 class="create-title">Create post</h4>
    <my-input
        v-model:value="post.title"
        placeholder="Name"
    >
    </my-input>
    <my-input
        v-model:value="post.body"
        class="create-input_desc"
        placeholder="Description"
    ></my-input>
    <my-button
        class="create-btn"
        @click="createPost"
    >
      Create post
    </my-button>
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
    }
  },

  methods: {
    createPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
      this.$emit('hideModal', false)
    }
  }
}
</script>

<style scoped>
  .create-title {
    margin: 10px 10px;
  }

  form {
    padding: 10px;
    display: flex;
    flex-direction: column;
    border-radius: 5px;
    margin: 20px 20px;
  }

  .create-input_desc {
    height: 100px;
  }

  .create-btn {
    border: 1px solid teal;
    color: teal;
    align-self: flex-end;
    margin: 10px 10px;
  }
</style>