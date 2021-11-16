<template>
  <select
    class="form-select rounded-0 mx-auto"
    @click="$emit('selectClick', $event.target.value)"
  >
    <option value="">All</option>
    <option v-for="(num, gen) in genreList" :key="gen" :value="gen">
      {{ gen }}
    </option>
  </select>
</template>

<script>
export default {
  name: "Select",
  props: {
    genreList: Object,
  },
};
</script>
