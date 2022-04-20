<template>
  <q-page class="column">
    <posts-container />
  </q-page>
</template>

<script lang="ts">
import PostsContainer from 'src/components/Posts/Posts.vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'MainPage',
  components: { PostsContainer },
});
</script>

<style lang="scss" scoped>
</style>
