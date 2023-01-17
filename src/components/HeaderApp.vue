<script>
export default {
  name: "HeaderApp",
  data() {
    return {
      userSearch: "",
    };
  },
};
</script>

<template>
  <!-- Ottengo il dato da cercare dall'input che sarà girato all'api grazie ad un Emit -->
  <div class="header">
    <div class="logo">
      <h1>Boolflix</h1>
    </div>

    <div class="search-wrapper">
      <input type="text" v-model="userSearch" placeholder="Cosa vuoi vedere?" />
      <button @click="$emit('search', userSearch)">Cerca</button>
    </div>
  </div>
</template>

<style lang="scss">
@use "../assets/styles/partials/variables" as *;

.header {
  height: 2rem;
  background-color: #656565;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 1rem;

  h1 {
    color: $netflixRed;
    text-transform: uppercase;
    font-weight: bold;
  }
}

div.search-wrapper input,
button {
  padding: 0.3rem;
  border: none;
}

div.search-wrapper button {
  margin-left: 0.5rem;
  background-color: $netflixRed;
  color: #fff;
  font-weight: bold;
}
</style>
