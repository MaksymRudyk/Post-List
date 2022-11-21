<template>
  <my-button @click="!visible">Cоздать Пост</my-button>
  <my-dialog :is-visible="visible" @click="openDialog">
    <PostForm
        @create="createPost"
    ></PostForm>
  </my-dialog>
  <PostList
      :posts="posts"
      @remove="deletePost"
  ></PostList>
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
    }
  },

  computed: {
     modalVisible: {
       return
     }
  }
}

</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>