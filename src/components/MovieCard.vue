<script>
import { store } from "../store";

export default {
  name: "MovieCard",
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div v-for="movie in store.movies">
    <h1>{{ movie.id }}</h1>
  </div>
</template>

<style lang="scss"></style>
