<template>
  <div>
    <h5>Создание поста</h5>
    <div class="q-gutter-sm form column">
      <q-input outlined v-model="post.title" label="Название" />
      <q-input outlined v-model="post.body" label="Описание" />
      <q-btn
        @click="createPost"
        class="form__btn"
        color="white"
        text-color="black"
        label="Создать"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PostForm',
  data() {
    return {
      post: {
        id: '',
        title: '',
        body: '',
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now().toString();
      this.$emit('create', this.post);
      this.post = {
        ...this.post,
        title: '',
        body: '',
      };
    },
  },
});
</script>

<style lang="scss" scoped>
.form {
  min-width: 500px;
  width: 100%;
  &__btn {
    margin-left: auto;
  }
}
</style>
