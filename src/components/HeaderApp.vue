<script>
export default {
  name: "HeaderApp",
  data() {
    return {
      movie: "",
    };
  },
};
</script>

<template>
  <input type="text" v-model="movie" />
  <button @click="$emit('search', movie)">Cerca</button>
</template>

<style lang="scss"></style>
