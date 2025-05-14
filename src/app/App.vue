<script setup lang="ts">
import { ref, onMounted } from 'vue';

import type { Post } from '../types/post';
import { PostList } from '../widgets/post-list';

const title = 'Application';

const posts = ref<Array<Post>>([]);
const fetching = ref<boolean>(false);

onMounted(async () => {
  fetching.value = true;
  await new Promise((resolve) => setTimeout(resolve, 500));
  posts.value = await fetch(
    'https://jsonplaceholder.typicode.com/posts?_limit=8'
  )
    .then((response) => response.json())
    .finally(() => (fetching.value = false));
});
</script>

<template>
  <main>
    <h1>{{ title }}</h1>
    <section class="section">
      <h2 class="section__title">Posts</h2>
      <PostList :posts="posts" :fetching="fetching" />
    </section>
  </main>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.section {
  background-color: antiquewhite;
  padding: 2rem;
  margin: 2rem 0;
}

.section__title {
  text-align: center;
  margin-bottom: 1.5rem;
}
</style>
