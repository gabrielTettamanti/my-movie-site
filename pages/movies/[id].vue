<script setup>
const route = useRoute();

const { data } = await useFetch(
  `https://www.omdbapi.com/?apikey=b79862fe&i=${route.params.id}`,
  {
    pick: ["Plot", "Title", "Poster"],
    key: `/movies/${route.params.id}`,
    onResponse({ request, response }) {
      if (response._data.Error === "Incorrect IMDb ID.") {
        showError({ statusCode: 404, statusMessage: "Page Not Found" });
      }
    },
  }
);
useHead({
  title: data.value.Title,
  meta: [
    { name: "description", content: data.value.Plot },
    { property: "og:description", content: data.value.Plot },
    { property: "og:image", content: data.value.Poster },
    { name: "twitter:card", content: `summary_large_image` },
  ],
});
</script>
<template>
  <section class="movie-detail-container">
    <div class="movie-detail-texts">
      <h1>{{data.Title}}</h1>
      <p>{{ data.Plot }}</p>
    </div>
    <div class="movie-detail-image-container">
      <img class="movie-detail-image" :src="data.Poster" :alt="data.Title">
    </div>
  </section>
</template>

<style lang="scss" scoped>
  .movie-detail-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    flex-wrap: wrap;
    margin: auto;
    width: 90%;
    max-width: 1200px;
    .movie-detail-texts {
      width: 60%;
      h1 {
        font-size: 24px;
      }
      p {
        font-size: 18px;
      }
    }
    .movie-detail-image-container {
      margin: 5%;
      .movie-detail-image {
        height: 70vh;
      }
    }
  }
  </style>