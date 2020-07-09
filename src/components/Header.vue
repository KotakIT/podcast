<template>
  <main class="pb-3">
    <img :src="image" width="90" class="float-left mr-3 rounded" />
    <h2 class="mb-0">{{ title }}</h2>
    <!-- <span>Obrolan it dan internet things</span> -->
    <span>{{ description }}</span>
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
