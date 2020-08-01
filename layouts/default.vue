<template>
  <div class="container">
    <Nuxt />
  </div>
</template>

<style lang="postcss">
html,
body,
.container {
  @apply h-screen;
}

body {
  margin: 0;
  overflow: hidden;
  color: #f4f4f4;
}

.container {
  @apply mx-auto;
}
</style>
