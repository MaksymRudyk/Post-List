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
        v-if="!isPostsLoading"
        :posts="posts"
        @remove="deletePost"
    ></PostList>
    <div v-else>
      Loading
    </div>
  </div>
</template>

<script>
import PostList from "@/components/PostList";
import PostForm from "@/components/PostForm";
import axios from "axios"
import MyButton from "@/components/UI/Mybutton";
export default {
  components: {
    MyButton,
    PostForm,
    PostList
  },
  data() {
    return {
      posts: [],
      modalVisible: false,
      isPostsLoading: false
    }
  },

  Mounted() {
    this.fetchPosts()
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

    async fetchPosts() {
      try {
        this.isPostsLoading = true
        setTimeout(async () => {
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
          this.posts = response.data
          this.isPostsLoading = false
        }, 1000)
      } catch (error) {
        console.log('Error:', error)
      }
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