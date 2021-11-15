<template>
  <div class="col">
    <div class="card border-0">
      <img :src="poster" class="card-img-top" :alt="title" />
      <div class="card-body text-center">
        <h4>{{ title.toUpperCase() }}</h4>
        <h5>{{ author }}</h5>
        <h6>{{ year }}</h6>
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
