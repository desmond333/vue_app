<template>
  <div class="posts">
    <h5>Рубрика "Посты"</h5>
    <post-form @create="createPost" />
    <div class="post-list">
      <post-item
        :post="post"
        v-for="post in posts"
        :key="post.id"
        @delete="deletePost"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import PostForm from './PostForm.vue';
import PostItem from './PostItem.vue';
import { TPost } from './types';

export default defineComponent({
  name: 'PostsContainer',
  components: {
    PostForm,
    PostItem,
  },

  data() {
    return {
      posts: [
        { id: '1', title: 'JS', body: 'Описание поста' },
        { id: '2', title: 'TS', body: 'Описание поста' },
        { id: '3', title: 'REACT', body: 'Описание поста' },
        { id: '4', title: 'VUE', body: 'Описание поста' },
        { id: '5', title: 'ANGULAR', body: 'Описание поста' },
      ],
    };
  },
  methods: {
    createPost(post: TPost) {
      this.posts.push(post);
    },
    deletePost(id: string) {
      this.posts = this.posts.filter((p) => p.id !== id);
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
