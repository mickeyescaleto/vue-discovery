<template>
  <div class="post-grid__card-skeleton" />
</template>

<style>
@keyframes pulse {
  0%,
  100% {
    opacity: 0.15;
  }
  50% {
    opacity: 0.1;
  }
}

.post-grid__card-skeleton {
  height: 10rem;
  background-color: darkgoldenrod;
  border-radius: 0.875rem;
  animation: pulse 1.5s ease-in-out infinite;
}
</style>
