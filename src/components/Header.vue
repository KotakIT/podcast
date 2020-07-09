<template>
  <main>
    <img :src="image" width="50" class="float-left mr-3" />
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>
  </main>
</template>

<script>
export default {
  props: {
    image: String,
    description: String,
    title: String,
  },
  name: "Header",
};
</script>

<style></style>
