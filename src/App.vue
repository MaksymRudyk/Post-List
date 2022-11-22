<template>
  <div class="app">
    <h1 style="margin: 10px 0">Post page</h1>
    <my-button
        @click="showDialog(true)" style="margin: 10px 0">Create post</my-button>
    <my-dialog v-model:isVisible="modalVisible">
      <PostForm
          @create="createPost"
          @hideModal="showDialog"
          v-model:isVisible="modalVisible"
      ></PostForm>
    </my-dialog>
    <PostList
        :posts="posts"
        @remove="deletePost"
    ></PostList>
  </div>
</template>

<script>
import PostList from "@/components/PostList";
import PostForm from "@/components/PostForm";

export default {
  components: {
    PostForm,
    PostList
  },
  data() {
    return {
      posts: [
        {
          id: 1,
          title: 'webPack',
          body: 'description 1'
        },
        {
          id: 2,
          title: 'Python',
          body: 'description 2'
        },
        {
          id: 3,
          title: 'Kotlin',
          body: 'description 3'
        }
      ],
      modalVisible: false
    }
  },

  methods: {
    createPost(post) {
      if (!!post.title && !!post.body) {
        this.posts.push(post)
      }
    },

    deletePost(post) {
      this.posts = this.posts.filter(item => item.id !== post.id)
    },

    showDialog(isVisible) {
      this.modalVisible = isVisible
    },
  },
}

</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .app {
    width: 90%;
    margin: auto;
  }
</style>