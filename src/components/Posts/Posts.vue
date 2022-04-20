<template>
  <div class="posts">
    <h5>Рубрика "Посты"</h5>
    <post-form @create="createPost" />
    <div class="post-list">
      <div v-for="post in posts" :key="post.id" @click="deletePost">
        <post :post="post" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import PostForm from './PostForm.vue';
import Post from './Post.vue';
import { TPost } from './types';

export default defineComponent({
  name: 'PostsContainer',
  components: {
    PostForm,
    Post,
  },

  data() {
    return {
      posts: [
        { id: 1, title: 'JS', body: 'Описание поста' },
        { id: 2, title: 'TS', body: 'Описание поста' },
        { id: 3, title: 'REACT', body: 'Описание поста' },
        { id: 4, title: 'VUE', body: 'Описание поста' },
        { id: 5, title: 'ANGULAR', body: 'Описание поста' },
      ],
    };
  },
  methods: {
    createPost(post: TPost) {
      this.posts.push(post);
    },
  },
});
</script>

<style lang="scss" scoped>
.posts {
  display: flex;
  flex-direction: column;
  gap: 40px;
}
</style>
