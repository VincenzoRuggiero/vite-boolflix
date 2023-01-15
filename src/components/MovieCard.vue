<script>
export default {
  name: "MovieCard",
  props: ["title", "originalTitle", "lang", "vote"], //Ricevo i props
  data() {
    return {};
  },
};
</script>

<template>
  <div class="card">
    <h2>{{ title }}</h2>
    <p>{{ originalTitle }}</p>
    <p>{{ lang }}</p>
    <p>{{ vote }}</p>
  </div>
</template>

<style lang="scss"></style>
