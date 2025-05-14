<script setup lang="ts">
import type { Post } from '../../../types/post';
import { PostCard, PostCardSkeleton } from '../../../components/ui/post-card';

const { posts, fetching } = defineProps<{
  posts: Array<Post>;
  fetching: boolean;
}>();

console.log(fetching);
</script>

<template>
  <div class="post-grid">
    <template v-if="!fetching">
      <PostCard v-for="post in posts" :key="post.id" :post="post" />
    </template>
    <template v-else>
      <PostCardSkeleton v-for="i in 8" :key="'post-card-skeleton-' + i" />
    </template>
  </div>
</template>

<style>
.post-grid {
  display: grid;
  grid-template-columns: repeat(1, minmax(0, 1fr));
  row-gap: 2rem;
  column-gap: 2rem;

  @media (width >= 48rem) {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  @media (width >= 64rem) {
    grid-template-columns: repeat(4, minmax(0, 1fr));
  }
}
</style>
