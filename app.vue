<script setup>
useHead({
  titleTemplate: (titleChunk) => {
    return titleChunk ? `${titleChunk} - My movie site` : "My movie site";
  },
});
</script>
<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>
<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&display=swap');
  $background: #0c0c0d;
  $primary-50: #F2FDF9;
  $primary-100: #E6FCF3;
  $primary-200: #BFF6E0;
  $primary-300: #99F1CD;
  $primary-400: #4DE7A8;
  $primary-500: #00DC82;
  $primary-600: #00C675;
  $primary-700: #00844E;
  $primary-800: #00633B;
  $primary-900: #004227;
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: 'DM Sans', sans-serif;
    letter-spacing: 0.06em;
    -webkit-tap-highlight-color: transparent;
    color: $primary-100;
  }
  body {
    background-color: $background;
  }
</style>