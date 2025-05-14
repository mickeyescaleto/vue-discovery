<script setup lang="ts">
import type { Post } from '../../../../types/post';

const { post } = defineProps<{
  post: Post;
}>();
</script>

<template>
  <div class="post-grid__card">
    <p :title="post.title" class="post-grid__title">{{ post.title }}</p>
    <p class="post-grid__body">{{ post.body }}</p>
  </div>
</template>

<style>
.post-grid__card {
  display: flex;
  flex-direction: column;
  row-gap: 0.5rem;
  padding: 1rem;
  background-color: bisque;
  border-radius: 0.875rem;
  height: 10rem;

  & > p {
    margin: 0;
  }
}

.post-grid__title {
  font-size: 1.25rem;
  font-weight: 500;
}

.post-grid__body {
  color: dimgray;
}
</style>
