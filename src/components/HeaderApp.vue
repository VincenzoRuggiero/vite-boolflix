<script>
export default {
  name: "HeaderApp",
  data() {
    return {
      userInput: "",
    };
  },
};
</script>

<template>
  <!-- Ottengo il dato da cercare dall'input che sarà girato all'api grazie ad un Emit -->
  <div>
    <input type="text" v-model="userInput" />
    <button @click="$emit('search', userInput)">Cerca</button>
  </div>
</template>

<style lang="scss"></style>
