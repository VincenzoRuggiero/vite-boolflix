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
  <div>
    <input type="text" v-model="userSearch" />
    <button @click="$emit('search', userSearch)">Cerca</button>
  </div>
</template>

<style lang="scss"></style>
