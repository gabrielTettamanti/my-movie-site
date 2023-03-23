<script setup>
const query = ref("marvel");
const movies = ref([]);
async function search() {
  const { Search } = await $fetch(
    `https://www.omdbapi.com/?i=tt3896198&apikey=b79862fe&s=${query.value}`
  );
  movies.value = Search;
}
search();
</script>

<template>
  <div class="movie-search">
    <form class="movie-search-form" @submit.prevent="search">
      <input class="movie-search-form-input"  type="text" v-model="query" />
      <button class="movie-search-form-button" >🔎</button>
    </form>
    <ul style="display: flex; flex-wrap: wrap; gap: 10px; list-style: none">
      <li v-for="movie in movies" :key="movie.imdbID">
        <NuxtLink :to="{ name: 'movies-id', params: { id: movie.imdbID } }">
          <img :src="movie.Poster" :alt="movie.title" width="100" />
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
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
  
  .movie-search{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    margin: auto;
    max-width: 1200px;
    .movie-search-form {
      margin: 20px;
      width: 90%;
      max-width: 400px;
      display: flex;
      justify-content: space-between;
      .movie-search-form-input{
        border: solid 4px $primary-700;
        border-radius: 50px;
        height: 40px;
        width: 89%;
        background-color: $background;
        font-size: 18px;
        padding: 5px;
        transition: .5s;
        outline: none;
        &:focus {
          border: solid 4px $primary-600;
          background-color: $primary-600;
          color: $background;
        }
      }
      .movie-search-form-button{
        border: solid 4px $primary-700;
        border-radius: 50px;
        height: 40px;
        width: 40px;
        background-color: $background;
        font-size: 18px;
        transition: .5s;
        &:hover {
          border: solid 4px $primary-600;
          background-color: $primary-600;
        }
      }
    }
  }
</style>
