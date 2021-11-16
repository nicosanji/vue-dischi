<template>
  <div class="col">
    <div class="card border-0 rounded-0">
      <img :src="poster" :alt="title" class="card-img-top rounded-0 p-3" />
      <div class="card-body d-flex flex-column text-center py-0">
        <h4 class="text-white pb-4">{{ title.toUpperCase() }}</h4>
        <h5 class="text-secondary mb-0">{{ author }}</h5>
        <p class="text-secondary">{{ year }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    poster: String,
    title: String,
    author: String,
    genre: String,
    year: String,
  },
};
</script>
