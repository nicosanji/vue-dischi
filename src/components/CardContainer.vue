<template>
  <div class="container">
    <div class="row">
      <Select></Select>
    </div>
    <div class="row row-cols-5 gy-5">
      <Card
        v-for="(cd, i) in cdList"
        :key="i"
        :author="cd.author"
        :title="cd.title"
        :year="cd.year"
        :poster="cd.poster"
        :genre="cd.genre"
      ></Card>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";
import Select from "./Select.vue";

export default {
  components: { Card, Select },
  name: "CardContainer",
  data() {
    return {
      cdList: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.cdList = resp.data.response;
      });
  },
};
</script>
