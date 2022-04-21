<template>
  <q-item class="post" clickable v-ripple>
    <q-item-section>
      <q-item-label class="post__title">{{ post.title }}</q-item-label>
      <q-item-label caption class="post__body"
        >{{ post.body }} {{ post.id }}</q-item-label
      >
    </q-item-section>
    <q-btn flat dense round icon="menu" @click="deletePost" />
  </q-item>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import { TPost } from './types';

export default defineComponent({
  name: 'PostList',
  props: {
    post: {
      type: Object as PropType<TPost>,
      required: true,
    },
  },
  methods: {
    deletePost() {
      this.$emit('delete', this.post.id);
    },
  },
});
</script>

<style lang="scss" scoped>
.post {
  margin-bottom: 30px;
  background: rgba(34, 174, 255, 0.758);
  color: white;

  &__body {
    color: white;
  }
}
</style>
